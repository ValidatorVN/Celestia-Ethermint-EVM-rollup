# Celestia-Ethermint-EVM-rollup

Cấu hình khuyến cáo:

    Ram: 8 GB RAM
    Chip: 4 Core
    Ổ cứng: 250 GB SSD Storage
    Băng thông: 1 Gbps for Download/100 Mbps for Upload
    
Sử dụng hệ điều hành Ubuntu 20.04
Cài đặt Golang 1.19 trở lên

1/ Cài đặt Roollkit:

    git clone https://github.com/celestiaorg/ethermint.git
    cd ethermint
    make install

2/ Chạy 1 bản Celestia light-node theo hướng dẫn ở đây: Lưu ý chọn bản Mocha cho dễ, hoặc xem video hướng dẫn chạy trên Youtube Node & Validator VietNam

    https://docs.celestia.org/nodes/light-node/
    
    bash init.sh
    
3/ Thêm thông tin và block height:

    NAMESPACE_ID=$(echo $RANDOM | md5sum | head -c 16; echo;)
    DA_BLOCK_HEIGHT=$(curl https://rpc-blockspacerace.pops.one/block | jq -r '.result.block.header.height')
    
Faucet token Mocha vào ví đã chạy node, sau đó chạy lệnh:

    ethermintd start --rollkit.aggregator true --rollkit.da_layer celestia --rollkit.da_config='{"base_url":"http://localhost:26659","timeout":60000000000,"gas_limit":6000000,"fee":6000}' --rollkit.namespace_id $NAMESPACE_ID --rollkit.da_start_height $DA_BLOCK_HEIGHT 
    
4/ Update...
