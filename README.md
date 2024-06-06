## Example usage

```yml
  action-openvpn3:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Install openvpn3 
        run: sudo apt-get install openvpn
      - name: Connect VPN
        uses: semirhodzic/action-openvpn3@master
        id: connect_vpn
        with:
          FILE_OVPN: '.github/vpn/config.ovpn'
          TLS_KEY: ${{ secrets.TLS_KEY }}
        env:
          CA_CRT: ${{ secrets.CA_CRT}}
          USER_CRT: ${{ secrets.USER_CRT }}
          USER_KEY: ${{ secrets.USER_KEY }}
```
