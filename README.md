# Roteiro Práticas Selenium

## Acadêmico

### 01-) Monte um script para acessar o curso de sistemas e para preencher o formulário

##### Comente o seu código

```python

from time import sleep
from selenium import webdriver

drive = webdriver.Chrome(executable_path='./chromedriver')

drive.get("https://www.google.com.br/")

pesquisar = drive.find_element_by_name("q")
pesquisar.send_keys("UNIMATER")
pesquisar.submit()

sleep(2)
click = drive.find_element_by_css_selector('#rso > div:nth-child(1) > div > div > div > div > div > div > div > div.yuRUbf > a > h3')
click.click()

sleep(2)
curso = drive.find_element_by_xpath('/html/body/form/div[3]/main/article[1]/div/section/div[2]/a[8]')
curso.click()

sleep(4)
nome = 'Arthur Lunkes'
email = 'arthur.lunkes2017@gmail.com'
telefone = '(46)99110-0092'
msg = 'Aqui é o Arthur'

form_nome = drive.find_element_by_xpath('//*[@id="txtNome"]')
form_nome.click()
form_nome.send_keys(nome)

form_email = drive.find_element_by_xpath('//*[@id="txtEmail"]')
form_email.click()
form_email.send_keys(email)

form_telefone = drive.find_element_by_xpath('//*[@id="txtTelefone"]')
form_telefone.click()
form_telefone.send_keys(telefone)

form_mensagem = drive.find_element_by_xpath('//*[@id="txtMensagem"]')
form_mensagem.click()
form_mensagem.send_keys(msg)

```

### 02-) Agora crie um script para assistir a palavra do coordenador (Vídeo do Youtube). Para interagir com o conteúdo do \<iframe\> (neste caso, o vídeo do YouTube) usando o  Selenium, é preciso mudar para o contexto do \<iframe\>. Para fazer isso, utilize o seguinte trecho de código

##### Comente o seu código

```python

from time import sleep
from selenium import webdriver

driver = webdriver.Chrome(executable_path= "./chromedriver")

driver.get("https://www.google.com.br/")

pesquisar = driver.find_element_by_name("q")
pesquisar.send_keys("UNIMATER")
pesquisar.submit()

sleep(2)
site_unimater = driver.find_element_by_css_selector('#rso > div:nth-child(1) > div > div > div > div > div > div > div > div.yuRUbf > a > h3')
site_unimater.click()

sleep(4)
curso = driver.find_element_by_xpath('/html/body/form/div[3]/main/article[1]/div/section/div[2]/a[8]')
curso.click()

sleep(4)
iframe = driver.find_element_by_css_selector('#palavradocoordenador > p.palavra-coordenador-wrapper > iframe')
driver.switch_to.frame(iframe)

botao_play = driver.find_element_by_xpath('/html/body/div/div/div[4]/button')
botao_play.click()

```

### 03-) Agora crie um script para acessar seu portal do aluno

##### Comente o seu código

```python

from time import sleep
from selenium import webdriver

drive = webdriver.Chrome(executable_path= './chromedriver')

drive.get("https://www.google.com.br/")

pesquisar = drive.find_element_by_name("q")
pesquisar.send_keys("UNIMATER")
pesquisar.submit()

sleep(2)
click = drive.find_element_by_css_selector('#rso > div:nth-child(1) > div > div > div > div > div > div > div > div.yuRUbf > a > h3')
click.click()

sleep(2)
aluno = drive.find_element_by_xpath('/html/body/form/div[3]/header/div[1]/div/nav[1]/a[1]')
aluno.click()

sleep(2)
primeira_aba = drive.window_handles[1]

drive.switch_to.window(primeira_aba)
print("Nome segunda aba =" + drive.title)

usuario = '12218196'
senha = '12218196'

sleep(6)
form_usuario = drive.find_element_by_xpath('/html/body/div/div[2]/div/div[2]/div/form/div[1]/div/input')
form_usuario.click()
form_usuario.send_keys(usuario)

form_senha = drive.find_element_by_xpath('/html/body/div/div[2]/div/div[2]/div/form/div[2]/div[1]/input')
form_senha.click()
form_senha.send_keys(senha)

acessar = drive.find_element_by_xpath('//*[@id="btn-login"]')
acessar.click()

```

### 04-) Utilize o Selenium para baixar o arquivo CSV de toda a série histórica, ou seja, de  todo o período – desde começo – até o dia atual, das ações das Americanas - AMER3.SA

##### Comente o seu código

```python

from time import sleep
from selenium import webdriver

driver = webdriver.Chrome(executable_path= './chromedriver')

driver.get('https://finance.yahoo.com/quote/AMER3.SA/history?p=AMER3.SA')

selecionar_data = driver.find_element_by_xpath('/html/body/div[1]/div/div/div[1]/div/div[3]/div[1]/div/div[2]/div/div/section/div[1]/div[1]/div[1]/div/div/div')
selecionar_data.click()

selecionar_data_max = driver.find_element_by_xpath('/html/body/div[1]/div/div/div[1]/div/div[3]/div[1]/div/div[2]/div/div/section/div[1]/div[1]/div[1]/div/div/div[2]/div/ul[2]/li[4]/button')
selecionar_data_max.click()

fazer_download = driver.find_element_by_xpath('/html/body/div[1]/div/div/div[1]/div/div[3]/div[1]/div/div[2]/div/div/section/div[1]/div[2]/span[2]/a')
fazer_download.click()

```

# DESAFIO

### 05-) Utilize o Selenium para baixar o arquivo CSV de toda a série histórica, ou seja, de  todo o período – desde começo – até o dia atual

### Para todas as empresas do setor de varejo

- AMER3.SA (Americanas)
- MGLU3.SA (Magazine)
- VIIA3.SA (Via - Casa Bahia, Ponto Frio)
- ALPA4.SA (Havaianas, Dupé)
- ARZZ3.SA (Arezzo, AnaCapri)
- CEAB3.SA (Abril Capital)
- SFBG3.SA (Centauro)
- GUAR3.SA (Riachuelo e Midway)
- SOMA3.SA (Hering)
- LREN3.SA (Renner)
- AMAR3.SA (Marisa)
- TFCO4.SA (Track Field)
- LJQQ3.SA (Quero-Quero)
- MBLY3.SA (Megastore)
- NTCO3.SA (Natura)
- PGMN3.SA (Petz)
- RADL3.SA (Raia)
- WEST3.SA  (Westwing)

##### Comente o seu código

```python

from time import sleep
from selenium import webdriver

driver = webdriver.Chrome(executable_path= './chromedriver')

lojas = ['AMER3.SA', 'MGLU3.SA', 'VIIA3.SA', 'ALPA4.SA',
         'ARZZ3.SA', 'CEAB3.SA', 'SFBG3.SA', 'GUAR3.SA',
         'SOMA3.SA', 'LREN3.SA', 'AMAR3.SA', 'TFCO4.SA',
         'LJQQ3.SA', 'MBLY3.SA', 'NTCO3.SA', 'PGMN3.SA',
         'RADL3.SA', 'WEST3.SA']

for loja in lojas:
    site = f'https://finance.yahoo.com/quote/{loja}/history?p={loja}'
    driver.get(site)

    sleep(2)
    selecionar_data = driver.find_element_by_xpath('/html/body/div[1]/div/div/div[1]/div/div[3]/div[1]/div/div[2]/div/div/section/div[1]/div[1]/div[1]/div/div/div')
    selecionar_data.click()

    sleep(2)
    selecionar_data_max = driver.find_element_by_xpath('/html/body/div[1]/div/div/div[1]/div/div[3]/div[1]/div/div[2]/div/div/section/div[1]/div[1]/div[1]/div/div/div[2]/div/ul[2]/li[4]/button')
    selecionar_data_max.click()

    sleep(2)
    fazer_download = driver.find_element_by_xpath('/html/body/div[1]/div/div/div[1]/div/div[3]/div[1]/div/div[2]/div/div/section/div[1]/div[2]/span[2]/a')
    fazer_download.click()

```