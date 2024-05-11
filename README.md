![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)![Selenium](https://img.shields.io/badge/-selenium-%43B02A?style=for-the-badge&logo=selenium&logoColor=white)
# D4sign-WebScrapping-Selenium
Raspagem de nome de documentos autonôma

### Automação de Coleta de Nomes de Documentos na Plataforma D4sign

Este script Python utiliza a biblioteca Selenium para automatizar a coleta de nomes de documentos na plataforma D4sign. Ele permite que você faça login na plataforma, obtenha o número total de documentos e, em seguida, raspe os nomes de todos os documentos disponíveis.

#### Pré-requisitos

Certifique-se de ter instalado os seguintes pacotes Python:

- `asyncio`
- `dotenv`
- `selenium`
- `webdriver_manager`

Você pode instalar esses pacotes executando:

```
pip install asyncio dotenv selenium webdriver_manager
```

#### Configuração

Antes de executar o script, é necessário configurar suas credenciais D4sign. Crie um arquivo `.env` no mesmo diretório do script e adicione as seguintes linhas:

```
email=seu_email
senha=sua_senha
```

Além disso, substitua `'url_dos_seus_cofres_d4sign'` na variável `url` com o URL dos seus cofres na plataforma D4sign.

#### Execução

Execute o script Python `automation.py` e ele irá:

1. Fazer login na plataforma D4sign.
2. Obter o número total de documentos.
3. Raspar os nomes de todos os documentos disponíveis.
4. Gerar um arquivo de texto com os nomes dos documentos.

#### Observações

- Certifique-se de que o Chrome WebDriver está instalado. Se não estiver, o script fará o download automaticamente.
- O script está configurado para executar em modo headless (sem interface gráfica). Se desejar visualizar a interface, altere `options.headless = True` para `options.headless = False`.
- O número total de documentos por página é definido como 20. Você pode ajustar esse valor conforme necessário.
- Certifique-se de substituir o URL correto na função `scrape_documents` para acessar as páginas corretas da plataforma D4sign.

---
**Disclaimer:** Este script foi desenvolvido para fins educacionais e pode precisar de ajustes dependendo das atualizações futuras na plataforma D4sign. Use-o com cuidado e sempre respeite os termos de serviço da plataforma.
