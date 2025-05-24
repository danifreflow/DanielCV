+++
date = '2025-05-11T15:58:50+02:00'
draft = false
title = 'Guts'
+++

En mi tiempo libre, disfruto mucho de ver series de animación japonesa online. Pero cada vez que intento acceder a una de las páginas web que hostean este tipo de contenido
me encuentro con un montón de anuncios y servicios innecesarios que hacen que mi conexión a internet se ralentice haciéndome no disfrutar de la experiencia. Por eso, una tarde decidí 
ponerme manos a la obra y cree Guts, un script de bash que te permite visualizar animación japonesa desde la comodidad de tu terminal UNIX.
El script esta disponible en [aqui](https://github.com/danifreflow/Guts)

![imagen-guts](/images/guts.png)

Este Script esta basado en el video de youtube de [anime desde terminal](https://www.youtube.com/watch?v=IHDqzGno4Y4) 
de [Houman](https://houmanr.xyz/) , tambien se inspira en proyectos angloparlantes como
[ani-cli](https://github.com/pystardust/ani-cli)

# Instalación
para instalarte el script en tu bash, descargate el archivo Guts y ejecuta los siguientes comandos:

```
sudo cp Guts /usr/bin && sudo chmod 755 /usr/bin/Guts
```


Asi podras usar Guts desde la terminal en cualquier momento.

## Funcionamineto del script
El script tiene las siguientes dependencias 
- grep
- wget
- mpv
- awk
- xargs
- ffmpeg


Actualmente recibe dos parametros de entrada **"titulo-del-anime-sin-espacion" "num-capitulo"**
Ejemplo para ver primer capitulo de bersek
```bash
./Guts.sh bersek 1
```
tambien hace busquedas de animes y te redirige al primer capitulo
```bash
./Guts.sh one
1
0 ah-my-goddess-2
1 baka-to-test-to-shoukanjuu-christmas-special
2 bayonetta-bloody-fate
3 c-the-money-of-soul-and-possibility-control
4 campione
5 chuukan-kanriroku-tonegawa
6 clione-no-akari
7 cutie-honey-universe
8 dr-stone
9 dr-stone-new-world
10 dr-stone-new-world-part-2
11 dr-stone-ryuusui
Presiona 'n' para seguir iterando, 'a' para retroceder si no pulsa el numero que quieres ver n
2
0 dr-stone-stone-wars
1 dragon-ball-z-movie-01-the-deadzone
2 evangelion-1-11-you-are-not-alone
3 fairy-gone
4 fairy-gone-2nd-season
5 ghost-in-the-shell-arise-border4-ghost-stands-alone
6 isekai-one-turn-kill-neesan-ane-douhan-no-isekai-seikatsu-hajimemashita
7 isekai-wa-smartphone-to-tomo-ni
8 isekai-wa-smartphone-to-tomo-ni-2
9 jojo-no-kimyou-na-bouken-part-6-stone-ocean
10 lv1-maou-to-one-room-yuusha
11 majin-bone
Presiona 'n' para seguir iterando, 'a' para retroceder si no pulsa el numero que quieres ver n
3
0 norn9-nornnonet
1 one-outs
2 one-piece
3 one-piece-3d2y-ace-no-shi-wo-koete-luffy-nakama-tono-chikai
4 one-piece-film-z
5 one-piece-film-gold
6 one-piece-film-red
7 one-piece-movie-14-stampede
8 one-piece-recap
9 one-piece-special-glorious-island
10 one-piece-adventure-of-nebulandia
11 one-piece-episode-of-luffy-hand-island-no-bouken
Presiona 'n' para seguir iterando, 'a' para retroceder si no pulsa el numero que quieres ver
```
Por ultimo, podemos usar la base de datos implementada con el flag -d

```
Guts -d
```

![ejemplo](/images/recording.gif)


Adjunto el video de [Houman](https://houmanr.xyz/) explicando la funcionalidad del script
{{< youtube bwtoPa-MnGI >}}
