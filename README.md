# Što je na radaru?
- radna verzija ET eksperimenta na temelju radarskih slika
- "Što je na radaru? ..." može biti i catchy naslov članka, npr.
  - What’s on the Radar? Eye-Tracking Evidence of Cognitive Flexibility in Dynamic Weather Visualizations
  - What’s on the Radar? Cognitive Flexibility and Visual Attention in Interpreting Meteorological Displays
  - What’s on the Radar? Rule Switching and Cognitive Flexibility in Meteorological Map Reading

## Kako pokrenuti
- koristiti index.html za ulaz u eksperiment
- završava s kraj.html
- logika se razlikuje kod onih koji su započeli s Low i High zadacima


# Kako izgleda flow
```
+------------------+
|   index.html      |
|  (START screen)   |
|  - participantId  |
|  - trialGroupId   |
|  - startBlock     |
+---------+--------+
          |
          |  if startBlock = LOW
          |------------------------------------+
          |                                    |
          v                                    v
+------------------+                   +------------------+
|  radar_L1.html    |                   |  radar_H1.html   |
+--------+---------+                   +--------+---------+
         |                                      |
         v                                      v
+------------------+                   +------------------+
|  radar_L2.html    |                   |  radar_H2.html   |
+--------+---------+                   +--------+---------+
         |                                      |
         v                                      v
+------------------+                   +------------------+
| nasa_tlx_L.html   |                   |  radar_H3a.html  |
| tlxBlock=LOW      |                   | (digits audio)   |
| sets: lowDone=1   |                   +--------+---------+
| lastBlock=LOW     |                            |
+--------+---------+                            v
         |                              +------------------+
         |                              |  radar_H3b.html   |
         |                              | (timed 60s)       |
         |                              +--------+---------+
         |                                       |
         |                                       v
         |                              +------------------+
         |                              |  radar_H3c.html   |
         |                              | (digit recall)    |
         |                              +--------+---------+
         |                                       |
         |                                       v
         |                              +------------------+
         |                              | nasa_tlx_H.html   |
         |                              | tlxBlock=HIGH     |
         |                              | sets: highDone=1  |
         |                              | lastBlock=HIGH    |
         |                              +--------+---------+
         |                                       |
         v                                       v
                  +------------------------------+
                  |          pauza.html          |
                  |  if (lowDone && highDone)    |
                  |        -> kraj.html          |
                  |  else if lastBlock=LOW       |
                  |        -> radar_H1.html      |
                  |  else if lastBlock=HIGH      |
                  |        -> radar_L1.html      |
                  +---------------+--------------+
                                  |
                                  v
                            +-----------+
                            |  kraj.html |
                            | export:    |
                            | JSON       |
                            | summary.csv|
                            | events.csv |
                            +-----------+
```

# Slike
- kompoziti se nalaze u folderu /img

# Ostali sadržaji
- audio zapis

# Procedura
- imamo dva L i tri H zadatka
