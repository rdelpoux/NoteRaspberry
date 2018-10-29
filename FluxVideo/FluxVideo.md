# Flux video Raspberry

## Flux video avec mplayer

### Côté Raspberry :

```console
raspivid -t 999999 -n -w 600 -h 600 -hf -fps 20 -o -| nc -l 9999
```

### Côté Ordinateur

```console
nc 192.168.0.20 9999 | mplayer -fps 200 -demuxer h264es -
```


