## Example usage

```yml
  connect-open-vpn:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Install Open VPN
        run: sudo apt-get install openvpn
      - name: Connect VPN
        uses: semirhodzic/action-openvpn3@master
        id: connect_vpn
        with:
          PING_URL: '127.0.0.1'
          FILE_OVPN: '.github/vpn/config.ovpn'
          SECRET: ${{ secrets.SECRET_USERNAME_PASSWORD }}
          TLS_KEY: ${{ secrets.TLS_KEY }}
        env:
          CA_CRT: ${{ secrets.CA_CRT}}
          USER_CRT: ${{ secrets.USER_CRT }}
          USER_KEY: ${{ secrets.USER_KEY }}
      - name: Check Connect VPN
        run: echo ${{ steps.connect_vpn.outputs.STATUS }}
```
