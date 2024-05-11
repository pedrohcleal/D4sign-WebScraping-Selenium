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

### Função `scrape_documents(driver, pags_num)` -> Detalhes

#### Parâmetros:
- `driver`: O objeto do WebDriver do Selenium, que permite a interação automatizada com o navegador.
- `pags_num`: O número total de páginas de documentos na plataforma D4sign.

#### Funcionamento:
1. **Iteração pelas Páginas:**
   - A função itera sobre cada página de documentos na plataforma, começando da página 0 até `pags_num - 1`.
   - Para cada página, o script acessa a URL correspondente à página de documentos, utilizando o método `driver.get()`.
   
2. **Espera pela Carregamento:**
   - Antes de começar a raspar os nomes dos documentos, o script espera um tempo (5 segundos) para garantir que a página esteja completamente carregada.

3. **Localização dos Elementos:**
   - Utilizando o método `driver.find_elements()`, a função localiza todos os elementos `<span>` que contêm o nome dos documentos.
   - Estes elementos são identificados pelo seletor CSS `"span[id^='nome_documento']"`, que encontra todos os elementos `<span>` cujo atributo `id` começa com `"nome_documento"`.
   
4. **Extração dos Nomes dos Documentos:**
   - Para cada elemento `<span>` encontrado, a função extrai o texto dentro das tags `<b>`, que representa o nome do documento.
   - Os nomes dos documentos são adicionados a uma lista chamada `list_names`.

5. **Contagem e Impressão:**
   - O script imprime o nome de cada documento à medida que é encontrado, além de informações adicionais como o número total de arquivos verificados até o momento e a página atual.
   - Isso permite que você monitore o progresso e verifique se a raspagem está ocorrendo conforme o esperado.

6. **Retorno da Lista de Nomes de Documentos:**
   - Após iterar por todas as páginas e coletar os nomes dos documentos, a função retorna a lista completa de nomes de documentos `list_names`.

#### Retorno:
- A função retorna uma lista contendo os nomes de todos os documentos presentes nas páginas da plataforma D4sign.

Essencialmente, a função `scrape_documents()` automatiza o processo de navegar pelas páginas de documentos na plataforma D4sign e extrair os nomes dos documentos para posterior processamento ou armazenamento.

---
**Disclaimer:** Este script foi desenvolvido para fins educacionais e pode precisar de ajustes dependendo das atualizações futuras na plataforma D4sign. Use-o com cuidado e sempre respeite os termos de serviço da plataforma.
