---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 04/10/2020
ms.openlocfilehash: 4ad0d7e54f93582237ed9457b562957018916d36
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463606"
---
# <a name="dotnet-new"></a>dotnet new

**Este artigo se aplica a:** ✔️ .NET Core 2.0 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a>Descrição

O `dotnet new` comando cria um projeto .NET Core ou outros artefatos baseados em um modelo.

O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.

## <a name="arguments"></a>Argumentos

- **`TEMPLATE`**

  O modelo para o qual criar uma instância quando o comando é invocado. Cada modelo pode ter opções específicas que podem ser passadas. Para obter mais informações, consulte [Opções de modelo](#template-options).

  Você pode `dotnet new --list` correr para ver uma lista de todos os modelos instalados. Se `TEMPLATE` o valor não for uma correspondência exata no texto na coluna **Modelos** ou **Nome Curto** da tabela retornada, uma correspondência de substring será realizada nessas duas colunas.

  Começando com o .NET Core 3.0 SDK, a CLI `dotnet new` procura modelos em NuGet.org quando você invoca o comando nas seguintes condições:

  - Se a CLI não conseguir encontrar uma `dotnet new`correspondência de modelo ao invocar, nem mesmo parcial.
  - Se houver uma versão mais recente do modelo disponível. Neste caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.

  O comando contém uma lista padrão de modelos. Use `dotnet new -l` para obter uma lista dos modelos disponíveis. A tabela a seguir mostra os modelos que vêm pré-instalados com o .NET Core SDK. O idioma padrão do modelo é mostrado entre parênteses. Clique no link nome curto para ver as opções específicas de modelo.

| Modelos                                    | Nome curto                      | Linguagem     | Marcas                                  | Introduzido |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Aplicativo do Console                          | [Console](#console)             | [C#], F#, VB | Comum/Console                        | 1.0        |
| Biblioteca de classes                                | [classlib](#classlib)           | [C#], F#, VB | Comum/Library                        | 1.0        |
| Aplicativo WPF                              | [Wpf](#wpf)                     | [C#]         | Comum/WPF                            | 3.0        |
| Biblioteca de classe WPF                            | [wpflib](#wpf)                  | [C#]         | Comum/WPF                            | 3.0        |
| Biblioteca de Controles Personalizados do WPF                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Comum/WPF                            | 3.0        |
| Biblioteca de controle de usuário WPF                     | [wpfusercontrollib](#wpf)       | [C#]         | Comum/WPF                            | 3.0        |
| Aplicativo Formulários do Windows (WinForms)         | [Winforms](#winforms)           | [C#]         | Formas comuns/winforms                       | 3.0        |
| Biblioteca de classes de Formulários do Windows (WinForms)       | [winformslib](#winforms)        | [C#]         | Formas comuns/winforms                       | 3.0        |
| Serviço ao Trabalhador                               | [Trabalhador](#web-others)           | [C#]         | Comum/Trabalhador/Web                     | 3.0        |
| Projeto de Teste de Unidade                            | [Mstest](#test)                 | [C#], F#, VB | Teste/MSTest                           | 1.0        |
| Projeto de Teste do NUnit 3                         | [Nunit](#nunit)                  | [C#], F#, VB | Teste/NUnit                            | 2.1.400    |
| Item de Teste do NUnit 3                            | `nunit-test`                    | [C#], F#, VB | Teste/NUnit                            | 2.2        |
| Projeto de Teste xUnit                           | [Xunit](#test)                  | [C#], F#, VB | Teste/xUnit                            | 1.0        |
| Componente da navalha                              | `razorcomponent`                | [C#]         | Web/ASP.NET                           | 3.0        |
| Página do Razor                                   | [Página](#page)                   | [C#]         | Web/ASP.NET                           | 2,0        |
| Importações de Exibição do MVC                              | [verimportações](#namespace)       | [C#]         | Web/ASP.NET                           | 2,0        |
| MVC ViewStart                                | `viewstart`                     | [C#]         | Web/ASP.NET                           | 2,0        |
| Aplicativo Blazor Server                            | [blazorserver](#blazorserver)   | [C#]         | Web/Blazor                            | 3.0        |
| ASP.NET Core Vazio                           | [Web](#web)                     | [C#], F#     | Web/Vazio                             | 1.0        |
| Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador) | [Mvc](#web-options)             | [C#], F#     | Web/MVC                               | 1.0        |
| Aplicativo Web ASP.NET Core                         | [webapp, navalha](#web-options)   | [C#]         | Web/MVC/Razor Pages                   | 2.2, 2.0   |
| ASP.NET Core com Angular                    | [angular](#spa)                 | [C#]         | Web/MVC/SPA                           | 2,0        |
| ASP.NET Core com React.js                   | [Reagir](#spa)                   | [C#]         | Web/MVC/SPA                           | 2,0        |
| ASP.NET Core com React.js e Redux         | [reactredux](#reactredux)       | [C#]         | Web/MVC/SPA                           | 2,0        |
| Biblioteca de Classes do Razor                          | [razorclasslib](#razorclasslib) | [C#]         | Web/Razor/Biblioteca/Biblioteca de Classes do Razor | 2.1        |
| API Web do ASP.NET Core                         | [webapi](#webapi)               | [C#], F#     | Web/WebAPI                            | 1.0        |
| ASP.NET Core gRPC Service                    | [grpc](#web-others)             | [C#]         | Web/gRPC                              | 3.0        |
| Arquivo de buffer de protocolo                         | [Proto](#namespace)             |              | Web/gRPC                              | 3.0        |
| dotnet arquivo gitignore                        | `gitignore`                     |              | Config                                | 3.0        |
| Arquivo global.json                             | [globaljson](#globaljson)       |              | Config                                | 2,0        |
| Configuração do NuGet                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| dotnet arquivo manifesto ferramenta local              | `tool-manifest`                 |              | Config                                | 3.0        |
| Configuração da Web                                   | `webconfig`                     |              | Config                                | 1.0        |
| Arquivo de Solução                                | `sln`                           |              | Solução                              | 1.0        |

## <a name="options"></a>Opções

- **`--dry-run`**

  Exibe um resumo do que aconteceria se o comando dado fosse executado. Disponível desde .NET Core 2.2 SDK.

- **`--force`**

  Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes. Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.

- **`-h|--help`**

  Imprime uma ajuda para o comando. Ele pode ser invocado para o `dotnet new` comando em si ou para qualquer modelo. Por exemplo, `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Instala um pacote de `PATH` `NUGET_ID` modelo si mesmo ou fornecido. Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`. Por `dotnet new` padrão, \* passa para a versão, que representa a versão mais recente do pacote estável. Veja um exemplo na seção [Exemplos.](#examples)
  
  Se uma versão do modelo já estiver instalada quando você executar este comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão foi especificada.

  Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).

- **`-l|--list`**

  Lista os modelos que contêm o nome especificado. Se nenhum nome for especificado, lista todos os modelos.

- **`-lang|--language {C#|F#|VB}`**

  A linguagem do modelo a ser criada. A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)). Não é válida para alguns modelos.

  > [!NOTE]
  > Alguns shells interpretam `#` como um caractere especial. Nesses casos, inclui o valor do parâmetro de idioma entre aspas. Por exemplo, `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  O nome para a saída criada. Se nenhum nome for especificado, o nome do diretório atual será usado.

- **`--nuget-source <SOURCE>`**

  Especifica uma origem do NuGet a ser usada durante a instalação. Disponível desde .NET Core 2.1 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Local para colocar a saída gerada. O padrão é o diretório atual.

- **`--type <TYPE>`**

  Filtra modelos com base em tipos disponíveis. Os valores `project` `item`predefinidos são, ou `other`.

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Desinstala um pacote `PATH` de `NUGET_ID` modelo no ou fornecido. Quando `<PATH|NUGET_ID>` o valor não é especificado, todos os pacotes de modelos instalados no momento e seus modelos associados são exibidos. Ao `NUGET_ID`especificar, não inclua o número da versão.

  Se você não especificar um parâmetro para essa opção, o comando listaos os modelos e detalhes instalados sobre eles.

  > [!NOTE]
  > Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho. Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.
  > Não inclua uma barra final de diretório de terminação no seu caminho de modelo.

- **`--update-apply`**

  Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala. Disponível desde o SDK do .NET Core 3.0.

- **`--update-check`**

  Verifique se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento. Disponível desde o SDK do .NET Core 3.0.

## <a name="template-options"></a>Opções de modelo

Cada modelo de projeto pode ter opções adicionais disponíveis. Os principais modelos têm as seguintes opções adicionais:

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. Disponível desde o SDK do .NET Core 3.0.

  A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:

  | Versão do SDK | Valor padrão   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Define `LangVersion` a propriedade no arquivo de projeto criado. Por exemplo, use `--langVersion 7.3` para usar C# 7.3. Sem suporte para F#. Disponível desde .NET Core 2.2 SDK.

  Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .

- **`--no-restore`**

  Se especificado, não executa uma restauração implícita durante a criação do projeto. Disponível desde .NET Core 2.2 SDK.

***

### <a name="classlib"></a>classlib

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard. O valor padrão é `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Define `LangVersion` a propriedade no arquivo de projeto criado. Por exemplo, use `--langVersion 7.3` para usar C# 7.3. Sem suporte para F#. Disponível desde .NET Core 2.2 SDK.

  Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a>wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. O valor padrão é `netcoreapp3.1`. Disponível desde .NET Core 3.1 SDK.

- **`--langVersion <VERSION_NUMBER>`**

  Define `LangVersion` a propriedade no arquivo de projeto criado. Por exemplo, use `--langVersion 7.3` para usar C# 7.3.

  Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

***

### <a name="winforms-winformslib"></a><a name="winforms"></a>winforms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Define `LangVersion` a propriedade no arquivo de projeto criado. Por exemplo, use `--langVersion 7.3` para usar C# 7.3.

  Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

***

### <a name="worker-grpc"></a><a name="web-others"></a>trabalhador, grpc

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. O valor padrão é `netcoreapp3.1`. Disponível desde .NET Core 3.1 SDK.

- **`--exclude-launch-settings`**

  Exclui *o lançamentoSettings.json* do modelo gerado.

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

***

### <a name="mstest-xunit"></a><a name="test"></a>mstest, xunit

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. Opção disponível desde .NET Core 3.0 SDK.

  A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:

  | Versão do SDK | Valor padrão   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  Permite a embalagem para o projeto usando [o pacote dotnet](dotnet-pack.md).

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

***

### <a name="nunit"></a>Nunit

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo.

  A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:

  | Versão do SDK | Valor padrão   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Permite a embalagem para o projeto usando [o pacote dotnet](dotnet-pack.md).

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

***

### <a name="page"></a>página

- **`-na|--namespace <NAMESPACE_NAME>`**

  Namespace para o código gerado. O valor padrão é `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Cria a página sem um PageModel.

***

### <a name="viewimports-proto"></a><a name="namespace"></a>verimportações, proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Namespace para o código gerado. O valor padrão é `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  O tipo de autenticação a ser usado. Os valores possíveis são:

  - `None` – Nenhuma autenticação (Padrão).
  - `Individual` – Autenticação individual.
  - `IndividualB2C` – Autenticação individual com o Azure AD B2C.
  - `SingleOrg` – Autenticação organizacional para um único locatário.
  - `MultiOrg` – Autenticação organizacional para vários locatários.
  - `Windows` – Autenticação do Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  A ocorrência B2C do Diretório Ativo do Azure para se conectar. Use com a autenticação do `IndividualB2C`. O valor padrão é `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  O id da política de inscrição e login para este projeto. Use com a autenticação do `IndividualB2C`.

- **`-rp|--reset-password-policy-id <ID>`**

  O iD da política de senha redefinida para este projeto. Use com a autenticação do `IndividualB2C`.

- **`-ep|--edit-profile-policy-id <ID>`**

  O ID de política de perfil de edição para este projeto. Use com a autenticação do `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  A instância do Diretório Ativo do Azure para se conectar. Use com a autenticação `SingleOrg` ou `MultiOrg`. O valor padrão é `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  O ID do Cliente para este projeto. Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`. O valor padrão é `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  O domínio para o inquilino do diretório. Use com a autenticação `SingleOrg` ou `IndividualB2C`. O valor padrão é `qualified.domain.name`.

- **`--tenant-id <ID>`**

  O ID TenantId do diretório para se conectar. Use com a autenticação do `SingleOrg`. O valor padrão é `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento. Use com a autenticação `SingleOrg` ou `IndividualB2C`. O valor padrão é `/signin-oidc`.

- **`-r|--org-read-access`**

  Permite que este aplicativo leia acesso ao diretório. Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.

- **`--exclude-launch-settings`**

  Exclui *o lançamentoSettings.json* do modelo gerado.

- **`--no-https`**

  Desativa https. Esta opção só `Individual`se `IndividualB2C` `SingleOrg`aplica `MultiOrg` se , , `--auth`ou não estiver sendo usado para .

- **`-uld|--use-local-db`**

  Especifica o LocalDB deve ser usado em vez de SQLite. Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Exclui *o lançamentoSettings.json* do modelo gerado.

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. Opção não disponível no .NET Core 2.2 SDK.

  A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:

  | Versão do SDK | Valor padrão   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

- **`--no-https`**

  Desativa https.

***

### <a name="mvc-webapp"></a><a name="web-options"></a>mvc, webapp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  O tipo de autenticação a ser usado. Os valores possíveis são:

  - `None` – Nenhuma autenticação (Padrão).
  - `Individual` – Autenticação individual.
  - `IndividualB2C` – Autenticação individual com o Azure AD B2C.
  - `SingleOrg` – Autenticação organizacional para um único locatário.
  - `MultiOrg` – Autenticação organizacional para vários locatários.
  - `Windows` – Autenticação do Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  A ocorrência B2C do Diretório Ativo do Azure para se conectar. Use com a autenticação do `IndividualB2C`. O valor padrão é `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  O id da política de inscrição e login para este projeto. Use com a autenticação do `IndividualB2C`.

- **`-rp|--reset-password-policy-id <ID>`**

  O iD da política de senha redefinida para este projeto. Use com a autenticação do `IndividualB2C`.

- **`-ep|--edit-profile-policy-id <ID>`**

  O ID de política de perfil de edição para este projeto. Use com a autenticação do `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  A instância do Diretório Ativo do Azure para se conectar. Use com a autenticação `SingleOrg` ou `MultiOrg`. O valor padrão é `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  O ID do Cliente para este projeto. Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`. O valor padrão é `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  O domínio para o inquilino do diretório. Use com a autenticação `SingleOrg` ou `IndividualB2C`. O valor padrão é `qualified.domain.name`.

- **`--tenant-id <ID>`**

  O ID TenantId do diretório para se conectar. Use com a autenticação do `SingleOrg`. O valor padrão é `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento. Use com a autenticação `SingleOrg` ou `IndividualB2C`. O valor padrão é `/signin-oidc`.

- **`-r|--org-read-access`**

  Permite que este aplicativo leia acesso ao diretório. Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.

- **`--exclude-launch-settings`**

  Exclui *o lançamentoSettings.json* do modelo gerado.

- **`--no-https`**

  Desativa https. Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.

- **`-uld|--use-local-db`**

  Especifica o LocalDB deve ser usado em vez de SQLite. Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. Opção disponível desde .NET Core 3.0 SDK.

  A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:

  | Versão do SDK | Valor padrão   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

- **`--use-browserlink`**

  Inclui o BrowserLink no projeto. Opção não disponível em .NET Core 2.2 e 3.1 SDK.

- **`-rrc|--razor-runtime-compilation`**

  Determina se o projeto está configurado para usar a [compilação Razor runtime](/aspnet/core/mvc/views/view-compilation#runtime-compilation) em compilações Debug. Opção disponível desde .NET Core 3.1 SDK.

***

### <a name="angular-react"></a><a name="spa"></a>angular, reagir

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  O tipo de autenticação a ser usado. Disponível desde o SDK do .NET Core 3.0.
  
  Os valores possíveis são:

  - `None` – Nenhuma autenticação (Padrão).
  - `Individual` – Autenticação individual.

- **`--exclude-launch-settings`**

  Exclui *o lançamentoSettings.json* do modelo gerado.

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

- **`--no-https`**

  Desativa https. Essa opção só se aplica `None`se a autenticação for .

- **`-uld|--use-local-db`**

  Especifica o LocalDB deve ser usado em vez de SQLite. Aplicável apenas à autenticação `Individual` ou `IndividualB2C`. Disponível desde o SDK do .NET Core 3.0.

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. Opção não disponível no .NET Core 2.2 SDK.

  A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:

  | Versão do SDK | Valor padrão   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  Exclui *o lançamentoSettings.json* do modelo gerado.

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. Opção não disponível no .NET Core 2.2 SDK.

  A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:

  | Versão do SDK | Valor padrão   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

- **`--no-https`**

  Desativa https.

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

- **`-s|--support-pages-and-views`**

  Suporta a adição de páginas e visualizações tradicionais de navalha, além de componentes para esta biblioteca. Disponível desde o SDK do .NET Core 3.0.

***
  
### <a name="webapi"></a>webapi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  O tipo de autenticação a ser usado. Os valores possíveis são:

  - `None` – Nenhuma autenticação (Padrão).
  - `IndividualB2C` – Autenticação individual com o Azure AD B2C.
  - `SingleOrg` – Autenticação organizacional para um único locatário.
  - `Windows` – Autenticação do Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  A ocorrência B2C do Diretório Ativo do Azure para se conectar. Use com a autenticação do `IndividualB2C`. O valor padrão é `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  O id da política de inscrição e login para este projeto. Use com a autenticação do `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  A instância do Diretório Ativo do Azure para se conectar. Use com a autenticação do `SingleOrg`. O valor padrão é `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  O ID do Cliente para este projeto. Use com a autenticação `IndividualB2C` ou `SingleOrg`. O valor padrão é `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  O domínio para o inquilino do diretório. Use com a autenticação `IndividualB2C` ou `SingleOrg`. O valor padrão é `qualified.domain.name`.

- **`--tenant-id <ID>`**

  O ID TenantId do diretório para se conectar. Use com a autenticação do `SingleOrg`. O valor padrão é `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Permite que este aplicativo leia acesso ao diretório. Só se `SingleOrg` aplica à autenticação.

- **`--exclude-launch-settings`**

  Exclui *o lançamentoSettings.json* do modelo gerado.

- **`--no-https`**

  Desativa https. `app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`. Essa opção só `IndividualB2C` se `SingleOrg` aplica se ou não estiver sendo usada para autenticação.

- **`-uld|--use-local-db`**

  Especifica o LocalDB deve ser usado em vez de SQLite. Só se `IndividualB2C` aplica à autenticação.

- **`-f|--framework <FRAMEWORK>`**

  Especifica a [estrutura](../../standard/frameworks.md) para o alvo. Opção não disponível no .NET Core 2.2 SDK.

  A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:

  | Versão do SDK | Valor padrão   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Não executa uma restauração implícita durante a criação do projeto.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  Especifica a versão do .NET Core SDK para usar no arquivo *global.json.*

***

## <a name="examples"></a>Exemplos

- Crie um projeto de aplicativo de console em C# especificando o nome do modelo:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Crie um projeto de aplicativo de console F# no diretório atual:

  ```dotnetcli
  dotnet new console -lang F#
  ```

- Criar um projeto de biblioteca de classe .NET padrão no diretório especificado:

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Crie um projeto de xUnit:

  ```dotnetcli
  dotnet new xunit
  ```

- Liste todos os modelos disponíveis para os modelos spa (Single Page Application, aplicativo de página única):

  ```dotnetcli
  dotnet new spa -l
  ```

- Liste todos os modelos que correspondem à substring *we*. Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.

  ```dotnetcli
  dotnet new we -l
  ```

- Tentativa de invocar o modelo correspondente a *ng*. Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.

  ```dotnetcli
  dotnet new ng
  ```

- Instale a versão 2.0 dos modelos SPA para ASP.NET Core:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Liste os modelos e detalhes instalados sobre eles, incluindo como desinstalá-los:

  ```dotnetcli
  dotnet new -u
  ```

- Crie um *global.json* no diretório atual definindo a versão SDK para 3.1.101:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Confira também

- [Modelos personalizados para dotnet new](custom-templates.md)
- [Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)
- [Repositório do GitHub de dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
- [Modelos disponíveis para dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
