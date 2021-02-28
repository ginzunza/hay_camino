# ¿hay camino?
Corrobora si existe, o no, forma de llegar al destino.

### Condiciones
* Los obstáculos o caminos recorridos se denotan con -1
* Los caminos disponibles se denotan con 0
* Se asumen matrices simétricas

```ruby
DIRECCIONES = [[0,1],[0,-1],[1,0],[-1,0]]# guarda las 4 posibilidades de movimientos ↓, ↑, →, ←

def hay_camino? camino
  rutas = []
  rutas << [0,0]
  
  until rutas.empty?
    p = rutas[0]
    rutas.shift
    return "Sí" if p[0] == camino.length - 1 && p[1] == camino.length - 1 
    
    DIRECCIONES.each do |d|
      x = p[0] + d[0]
      y = p[1] + d[1]
      rutas << [x,y] if x >= 0 && y >= 0 && x < camino.length && y < camino.length && camino[x][y] != -1 
    end
  end
  "No"
end
```
### Ejemplo

```ruby
camino =[
  [0,0,0],
  [0,0,0],
  [0,0,0]
]
hay_camino? camino # => Sí

camino =[
  [0,-1],
  [-1,0],
]
hay_camino? camino # => No


```
