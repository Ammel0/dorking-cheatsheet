# Guia Completo de Google Dorking: Operadores, Sintaxe, Exemplos e Aplicações em Segurança

## O que é Google Dorking?

> **Google Dorking** (Google Hacking, ou simplesmente, Dorking) é uma técnica de busca avançada que utiliza operadores específicos no Google para encontrar informações que não são normalmente acessadas por pesquisas comuns. É frequentemente usada em *OSINT* para captar informações sensiveis que porventura estão desprotegidas.
---

Essa técnica é amplamente usada para:
- Encontrar arquivos confidenciais (senhas, backups, logs)
- Descobrir diretórios e dispositivos expostos
- Realizar testes de segurança (pentest)
- Coletar informações via OSINT
- Localizar arquivos sensíveis (.sql, .txt, .xls, etc.)
- Encontrar diretórios listados
- Descobrir dispositivos IoT expostos
- Identificar falhas de configuração
- Coletar e-mails e metadados
- Fazer footprinting de alvos em auditorias de segurança

---

## Tabela de Operadores Google Dorking

| Operador           | Descrição                                                                 | Exemplo                                      |
|--------------------|---------------------------------------------------------------------------|----------------------------------------------|
| `site:`            | Restringe a busca a um domínio específico                                  | `site:gov.br`                                |
| `inurl:`           | Busca por URLs que contenham a palavra-chave                              | `inurl:admin`                                |
| `intitle:`         | Busca por páginas com o termo no título                                   | `intitle:"index of"`                         |
| `intext:`          | Busca por palavras no conteúdo da página                                  | `intext:"confidential"`                      |
| `filetype:`        | Busca por arquivos com uma extensão específica                            | `filetype:pdf "relatório anual"`             |
| `ext:`             | Sinônimo de `filetype:`                                                    | `ext:xls site:example.com`                   |
| `cache:`           | Mostra a versão em cache da página pelo Google                            | `cache:example.com`                          |
| `link:`            | Mostra páginas que contêm links para um site                              | `link:example.com`                           |
| `related:`         | Busca por sites similares                                                  | `related:youtube.com`                        |
| `allinurl:`        | Todos os termos devem estar na URL                                         | `allinurl:admin login`                       |
| `allintitle:`      | Todos os termos devem estar no título                                      | `allintitle:relatório financeiro 2024`       |
| `allintext:`       | Todos os termos devem estar no corpo do texto                              | `allintext:senha usuário`                    |
| `allinanchor:`     | Termos devem aparecer no texto de âncoras (links)                          | `allinanchor:"login privado"`                |
| `"aspas"`          | Busca exata da frase                                                       | `"confidential information"`                 |
| `-palavra`         | Exclui resultados com o termo                                              | `login -facebook`                            |
| `OR` / `|`         | Combina termos (um ou outro)                                               | `admin OR login` ou `admin | login`         |
| `AND`              | Todos os termos devem estar presentes                                      | `filetype:pdf AND orçamento`                 |
| `*` (curinga)      | Substitui qualquer palavra                                                 | `"senha * root"`                             |
| `( )`              | Agrupa termos ou operadores                                                | `(login OR senha) site:br`                   |
| Im Feeling Lucky   | Acessa diretamente a primeira pagina encontrada na pesquisa.               | "wikipedia" = wikipedia.org/wiki/Main_page   |
| `define:`          | Retorna definições da palavra                                              | "define: world" /wər(ə)ld/, noun 1. the earth, together with all of its countries, peoples, and natural features. (etc)|

---

## Exemplos de Consultas avançadas recorrentes:

##### - Buscar documentos confidenciais por tipo e conteúdo
`filetype:pdf | filetype:xls | filetype:doc "confidencial" OR "internal"`

##### - Encontrar arquivos com senhas expostas
`intitle:"index of" (passwords.txt | credentials.csv | config.php)`

##### - Coletar e-mails corporativos de um domínio
`site:empresaalvo.com.br intext:"@empresaalvo.com.br"`

##### - Encontrar diretórios de backup e exportações
`intitle:"index of" (backup | .sql | export)`

##### - Pegar mensagens de erro que revelam tecnologia ou versão
`intext:"Warning: mysql_fetch" | intext:"Deprecated: Function" site:.br`

##### - Localizar câmeras IP acessíveis publicamente
`inurl:/view/index.shtml | inurl:top.htm intext:"camera"`

##### - Encontrar páginas de administração
´inurl:admin OR inurl:login intitle:"admin panel"´

##### - Localizar arquivos de configuração (.env, .ini, .bak)
`inurl:.env | inurl:.ini | filetype:bak`

##### - Buscar imagens com metadados sensíveis
`site:imgur.com filetype:jpg OR filetype:png "confidencial"`

##### - Detectar CMS e suas falhas
`inurl:wp-content OR inurl:joomla intitle:"index of"`

##### - Localizar arquivos de log abertos
`intitle:"index of" (log.txt | error.log | access.log)`

##### - Descobrir links internos de sistemas privados
`site:intranet.empresa.com.br inurl:dashboard OR inurl:status`

##### - Encontrar documentos de RH e currículos
`filetype:pdf (currículo OR "curriculum vitae") site:empresa.com`

##### - Listar repositórios e arquivos de versão
`intitle:"index of" (.git | .svn | .hg)`

##### - Verificar exposições em subdomínios
`site:*.empresa.com -www`

##### - Combinar múltiplas técnicas para buscas refinadas
`site:empresa.com filetype:xls intext:"senha" inurl:restrito`

---

### Para aproveitar outras consultas prontas:
A *Google Hacking Database (GHDB)* é mantida pela Offensive Security e traz uma vasta coleção de *dorks* categorizados para resultados especificos.

[Link dos Dorks por ExploitDB](https://www.exploit-db.com/google-hacking-database)

--- 

⚠️ Aviso Legal
Este conteúdo é exclusivamente para fins educacionais e de teste controlado.
O uso em ambientes não autorizados pode ser crime digital e causar implicações legais graves.

---

### Contribua com novos dorks por Pull Request!

