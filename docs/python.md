#**Códigos  em Python**

🐍
---

###Merge Sort
~~~python
def merge_sort(arr):
  print(arr)
  if len(arr) <= 1:
    return arr
  mid = len(arr) // 2
  left_half = arr[:mid]
  right_half = arr[mid:]

  left_sorted = merge_sort(left_half)
  right_sorted = merge_sort(right_half)

  return merge(left_sorted, right_sorted)
def merge(left, right):
  result = []
  i = j = 0
  while i < len(left) and j < len(right):
    if left[i] < right[j]:
      result.append(left[i])
      i += 1
    else:
      result.append(right[j])
      j += 1

  result.extend(left[i:])
  result.extend(right[j:])
  return result
def listint(lst):
  lista = []
  for i in lst:
    lista.append(int(i))
  return lista

aux = input().split()
lista = listint(aux)
print(lista)
ord_lista = merge_sort(lista)
print(ord_lista)
~~~

###Pesquisa Binária (recursiva)
~~~python
def bsr(l, e, d, x):
   if e <= d:
       m = (e+d)//2
       print(l[0:m])
       if x == l[m]:
           return m
       elif l[m] > x:
           return bsr(l, e, m-1, x)
       else:
           return bsr(l, m+1, d, x)
   else:
       return -1

l = [int(i) for i in input().split()]
print(l)
n = int(input())
e = 0
d = len(l) - 1
r = bsr(l, e, d, n)
if r == -1:
   print("ausente")
else:
   print("posição:", r)
~~~

###Orientação à objetos
~~~python
mport csv

colunas = ['Name', 'Price', 'Quantidy']  # Nomes das colunas
dados = [
    ["Phone", 100, 5],
    ["Laptop", 1000, 3],
    ["Cable", 10, 5],
    ["Mouse", 50, 5],
    ["Keyboard", 75, 5],
]

with open('dados.csv', mode='w', newline='', encoding='utf-8') as arquivo_csv:
    escritor = csv.writer(arquivo_csv)
    escritor.writerow(colunas)  # Nomes das colunas
    escritor.writerows(dados)   # Dados

# ----------------------------------------------------------------------------------------------------------------------------------

class Item:
    pay_rate = 0.8  # A taxa de pagamento depois de 20% de desconto
    all = []

    def __init__(self, name: str, price: float, qnt=0):  # no caso da qnt, como eu associei o default a 0 ele já assumiu que só pode valores inteiros
        # Run validations to the received arguments
        assert price >= 0, "Erro pois o preço é negativo"
        assert qnt >= 0, "Erro pois a quantidade ´negativa"

        # Assign to self object
        self.name = name
        self.price = price
        self.quantidy = qnt

        # Actions to execute
        Item.all.append(self)

    def total_price(self):
        return self.quantidy * self.price

    def __repr__(self):
        return f"Item('{self.name}', {self.price}, {self.quantidy})"

    def apply_discount(self):
        self.price = self.price * self.pay_rate

    @classmethod  # Ta dizendo que é um método da classe e não do objeto
    def instantiate_from_csv(cls):  # Pelo que eu entendi, ta pegando aquele protótipo e banco de dados e jogando pra ca, mas dps tenho que pesquisar melhor
        with open('dados.csv', 'r', encoding='utf-8') as f:  # leitura do CSV
            reader = csv.DictReader(f)
            items = list(reader)
        for item in items:
            Item(
                name=item.get('Name'),
                price=float(item.get('Price')),
                qnt=int(item.get('Quantidy'))
            )
        print(items)

    @staticmethod
    def is_integer(num):
        # We will count out the floats that are point zero
        # For i.e: 5.0, 10.0
        if isinstance(num, float):
            # Count out the floats that are point zero
            return num.is_integer()
        elif isinstance(num, int):
            return True
        else:
            return False

print(Item.is_integer(3))
Item.instantiate_from_csv()
~~~