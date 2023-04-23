brew install koekeishiya/formulae/yabai
brew services start yabai



brew services restart yabai brew services info yabai
brew remove yabai


# Install skhd
brew install koekeishiya/formulae/skhd
# Start skhd
brew services start skhd


## Debug
yabai -m config debug_output on
```bash
# directory containing log files (HOMEBREW_PREFIX defaults to /usr/local unless you manually specified otherwise)
HOMEBREW_PREFIX/var/log/yabai/
/usr/local/var/log/yabai

# view the last lines of the error log 
tail -f /usr/local/var/log/yabai/yabai.err.log

# view the last lines of the debug log
tail -f /usr/local/var/log/yabai/yabai.out.log
```


```bash
# Web browsers
yabai -m rule --add app="^Google Chrome|Firefox$" space=1
# Text editors
yabai -m rule --add app="^(Code|RStudio)$" space=2
# Jetbrains apps
apps="^(IntelliJ IDEA|WebStorm|RubyMine|PyCharm|DataGrip)$"
yabai -m rule --add app="${apps}" space=3  manage=off
# Terminal
yabai -m rule --add app="^(Alacritty)$" space=4
# Music
yabai -m rule --add app="^(Spotify|Amazon Music)$" space=5
# Social
yabai -m rule --add app="^(Slack|WhatsApp|Microsoft Teams)$" space=6

```


brew install cmacrae/formulae/spacebar
brew services start spacebar

- switching between stack and bsp mode
```bash
 ctrl + shift - space : yabai -m space --layout "$(yabai -m query --spaces --space | jq -r 'if .type == "bsp" then "stack" else "bsp" end')"
```

```bash
# focus window in bsp mode
alt - h: yabai -m window --focus west
alt - j: yabai -m window --focus south
alt - k: yabai -m window --focus north
alt - l: yabai -m window --focus east

# In stack mode
alt + p: yabai -m window --focus stack.prev
alt - n: yabai -m window --focus stack.next
alt - f: yabai -m window --focus stack.first
alt - g: yabai -m window --focus stack.last

```
## or use custom focus windows (preffered)
```
# forward
ctrl + shift - right : yabai -m query --spaces --space \
  | jq -re ".index" \
  | xargs -I{} yabai -m query --windows --space {} \
  | jq -sre "add | map(select(.minimized != 1)) | sort_by(.display, .frame.y, .frame.x, .id) | reverse | nth(index(map(select(.focused == 1))) - 1).id" \
  | xargs -I{} yabai -m window --focus {}

# backward
ctrl + shift - left: yabai -m query --spaces --space \
  | jq -re ".index" \
  | xargs -I{} yabai -m query --windows --space {} \
  | jq -sre "add | map(select(.minimized != 1)) | sort_by(.display, .frame.y, .frame.y, .id) | nth(index(map(select(.focused == 1))) - 1).id" \
  | xargs -I{} yabai -m window --focus {}
```

### Switching spaces
```
# fast focus desktop
ctrl - left : yabai -m space --focus prev
ctrl - right : yabai -m space --focus next
ctrl - z : yabai -m space --focus recent
ctrl - 1 : yabai -m space --focus 1
ctrl - 2 : yabai -m space --focus 2
ctrl - 3 : yabai -m space --focus 3
ctrl - 4 : yabai -m space --focus 4
ctrl - 5 : yabai -m space --focus 5
ctrl - 6 : yabai -m space --focus 6
ctrl - 7 : yabai -m space --focus 7
ctrl - 8 : yabai -m space --focus 8
ctrl - 9 : yabai -m space --focus 9
ctrl - 0 : yabai -m space --focus 10
```

## Moving to space
```bash
ctrl + shift - 1 : yabai -m window --space  1; yabai -m space --focus 1
ctrl + shift - 2 : yabai -m window --space  2; yabai -m space --focus 2
ctrl + shift - 3 : yabai -m window --space  3; yabai -m space --focus 3
ctrl + shift - 4 : yabai -m window --space  4; yabai -m space --focus 4
ctrl + shift - 5 : yabai -m window --space  5; yabai -m space --focus 5
ctrl + shift - 6 : yabai -m window --space  6; yabai -m space --focus 6
ctrl + shift - 7 : yabai -m window --space  7; yabai -m space --focus 7
ctrl + shift - 8 : yabai -m window --space  8; yabai -m space --focus 8
ctrl + shift - 9 : yabai -m window --space  9; yabai -m space --focus 9
ctrl + shift - 0 : yabai -m window --space 10; yabai -m space --focus 10
```

## References
- jessi skelton https://www.youtube.com/watch?v=JL1lz77YbUE
- https://www.youtube.com/watch?v=sFe9BwZ6Q6c
- https://anuj-chandra.medium.com/using-i3-like-tiling-window-managers-in-macos-with-yabai-ebf0e002b992
- repo https://github.com/koekeishiya/yabai
- wiki https://github.com/koekeishiya/yabai/wiki
- wiki https://github.com/koekeishiya/yabai/wiki/Disabling-System-Integrity-Protection
- https://faun.pub/yabai-macos-tile-window-manager-833ce1be396a
- spacebar https://github.com/cmacrae/spacebar





## Jessie setup
61 276 wyświetleń  27 lis 2020
Leave a comment if you have any questions! I'm sure i missed something..
---------------------------------------------------------------------------------------------------------
All my notes for this video 🖥️  : https://www.notion.so/Yabai-8da3b8298...
https://www.notion.so/Yabai-8da3b829872d432fac43181b7ff628fc
---------------------------------------------------------------------------------------------------------
Homebrew Video : https://youtu.be/dlYvElCeOmI
Karabiner Video Part 1 : https://youtu.be/uaJSjgVEhMQ
Karabiner Video Part 2 : https://youtu.be/PBPS2D9AKtI
---------------------------------------------------------------------------------------------------------
Yabai : https://github.com/koekeishiya/yabai
Limelight (standalone) : https://github.com/koekeishiya/limelight
Skhd : https://github.com/koekeishiya/skhd
Stackline : https://github.com/AdamWagner/stackline
---------------------------------------------------------------------------------------------------------
Lovely by Amine Maxwell https://soundcloud.com/aminemaxwell
Creative Commons — Attribution 3.0 Unported — CC BY 3.0
Free Download / Stream: http://bit.ly/lovely-amine-maxwell
Music promoted by Audio Library https://youtu.be/xkM0Ygic0Vg


### Steps
1. Install limelight
   download and build from https://github.com/koekeishiya/limelight
   
ln -s ~/myInstall/limelight-master/bin/limelight /usr/local/bin/limelight

/usr/local/bin/limelight --config 
2. install yabai and skhd
brew install koekeishiya/formulae/yabai
brew services start yabai
brew services restart yabai brew services info yabai
brew remove yabai

3.  Install skhd
> brew install koekeishiya/formulae/skhd
Start skhd
> brew services start skhd

4. Try stackline
    https://github.com/AdamWagner/stackline

5. Install https://hyperkey.app/