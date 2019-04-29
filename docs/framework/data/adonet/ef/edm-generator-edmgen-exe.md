---
title: Gerador de EDM (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 7f06b393cd7e7ccf3d3637d6fb46eb6d983d943a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607665"
---
# <a name="edm-generator-edmgenexe"></a>Gerador de EDM (EdmGen.exe)

A EdmGen.exe é uma ferramenta de linha de comando utilizada ao se trabalhar com o modelo e arquivos de mapeamento do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Você pode usar a ferramenta EdmGen.exe para:

- Conectar-se a uma fonte de dados, usando um provedor de dados do .NET Framework específico da fonte de dados, e gerar o modelo conceitual (.csdl), o modelo de armazenamento (.ssdl) e os arquivos (.msl) de mapeamento que são utilizados pelo [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Para obter mais informações, confira [Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

- Validar um modelo existente. Para obter mais informações, confira [Como: Use EdmGen.exe para validar o modelo e arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).

- Gerar um arquivo C# ou de código Visual Basic que contém as classes de objeto geradas a partir de um arquivo de modelo conceitual (.csdl). Para obter mais informações, confira [Como: Use EdmGen.exe para gerar o código da camada de objeto](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md).

- Gerar um arquivo C# ou de código Visual Basic que contém as exibições pré-geradas para um modelo existente. Para obter mais informações, [como: Gerar previamente exibições para melhorar o desempenho de consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).

A ferramenta EdmGen.exe é instalada no diretório do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Muitas vezes, está localizada em C:\windows\Microsoft.NET\Framework\v4.0. Para sistemas de 64 bits, está localizada em C:\windows\Microsoft.NET\Framework64\v4.0. Você também pode acessar a ferramenta EdmGen.exe do prompt de comando do Visual Studio (clique em **inicie**, aponte para **todos os programas**, aponte para **Microsoft Visual Studio 2010**, aponte para **Ferramentas do visual Studio**e, em seguida, clique em **Prompt de comando do Visual Studio 2010**).

## <a name="syntax"></a>Sintaxe

```
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Modo

Ao usar a ferramenta EdmGen.exe, você deve especificar um dos modos a seguir.

|Modo|Descrição|
|----------|-----------------|
|`/mode:ValidateArtifacts`|Valida arquivos .msl, .ssdl e .csdl, e exibe todos os erros ou avisos.<br /><br /> Esta opção requer pelo menos um dos argumentos `/inssdl` ou `/incsdl`. Se `/inmsl` estiver especificado, os argumentos `/inssdl` e `/incsdl` também serão obrigatórios.|
|`/mode:FullGeneration`|Usa informações de conexão de banco de dados especificadas na opção `/connectionstring` e gera .csdl, .ssdl, .msl, camada de objeto e arquivos de exibição.<br /><br /> Esta opção requer um argumento `/connectionstring` e um argumento `/project` ou os argumentos `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace` e `/entitycontainer`.|
|`/mode:FromSSDLGeneration`|Gera arquivos .csdl e .msl, código-fonte, e exibe no arquivo .ssdl especificado.<br /><br /> Esta opção requer o argumento `/inssdl` e um argumento `/project` ou os argumentos `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` e `/entitycontainer`.|
|`/mode:EntityClassGeneration`|Cria um arquivo de código-fonte que contém as classes geradas a partir do arquivo csdl.<br /><br /> Esta opção requer o argumento `/incsdl` e o argumento `/project` ou o argumento `/outobjectlayer`. O argumento `/language` é opcional.|
|`/mode:ViewGeneration`|Cria um arquivo de código-fonte que contém as exibições geradas a partir dos arquivos .csdl, .ssdl e .msl.<br /><br /> Esta opção requer os argumentos `/inssdl`, `/incsdl`, `/inmsl,` e `/project` ou `/outviews`. O argumento `/language` é opcional.|

## <a name="options"></a>Opções

|Opção|Descrição|
|------------|-----------------|
|`/p[roject]:`\<string>|Especifica o nome do projeto a ser usado. O nome do projeto é usado como um padrão para configuração de namespace, nome do modelo e arquivos de mapeamento, nome do arquivo de código-fonte do objeto e nome do arquivo de código-fonte de geração de exibição. O nome do contêiner de entidade é definido como \<projeto > contexto.|
|`/prov[ider]:`\<string>|O nome do provedor de dados do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] que será usado para gerar o arquivo (.ssdl) de modelo de armazenamento. O provedor padrão é o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider para SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|
|`/c[onnectionstring]:`\<cadeia de caracteres de conexão >|Especifica a cadeia de caracteres usada para se conectar à fonte de dados.|
|`/incsdl:`\<file>|Especifica o arquivo .csdl ou um diretório em que os arquivos .csdl estão localizados. Esse argumento pode ser especificado várias vezes para que você possa especificar vários diretórios ou arquivos .csdl. Especificar vários diretórios pode ser útil para gerar classes (`/mode:EntityClassGeneration`) ou exibições (`/mode:ViewGeneration`) quando o modelo conceitual é dividido em vários arquivos. Isso também pode ser útil quando você quiser validar vários modelos (`/mode:ValidateArtifacts`).|
|`/refcsdl:`\<file>|Especifica o arquivo .csdl ou arquivos adicionais usados para solucionar todas as referências no arquivo de código-fonte .csdl. (O arquivo de código-fonte .csdl é o arquivo especificado pela opção `/incsdl`). O arquivo `/refcsdl` contém tipos de que o arquivo de código-fonte .csdl depende. Esse argumento pode ser especificado várias vezes.|
|`/inmsl:`\<file>|Especifica o arquivo .msl ou um diretório em que os arquivos .msl estão localizados. Esse argumento pode ser especificado várias vezes para que você possa especificar vários diretórios ou arquivos .msl. Especificar vários diretórios pode ser útil para gerar exibições (`/mode:ViewGeneration`) quando o modelo conceitual é dividido em vários arquivos. Isso também pode ser útil quando você quiser validar vários modelos (`/mode:ValidateArtifacts`).|
|`/inssdl:`\<file>|Especifica o arquivo .ssdl ou um diretório em que os arquivos .ssdl estão localizados. Esse argumento pode ser especificado várias vezes para que você possa especificar vários diretórios ou arquivos .ssdl. Isso pode ser útil quando você quiser validar vários modelos `(/mode:ValidateArtifacts)`.|
|`/outcsdl:`\<file>|Especifica o nome do arquivo. csdl que será criado.|
|`/outmsl:`\<file>|Especifica o nome do arquivo .msl que será criado.|
|`/outssdl:`\<file>|Especifica o nome do arquivo .ssdl que será criado.|
|`/outobjectlayer:`\<file>|Especifica o nome do arquivo de código-fonte que contém os objetos gerados a partir do arquivo .csdl.|
|`/outviews:`\<file>|Especifica o nome do arquivo de código-fonte que contém as exibições geradas.|
|`/language:`[VB&#124;CSharp]|Especifica a linguagem dos arquivos de código-fonte gerados. A linguagem volta automaticamente para C#.|
|`/namespace:`\<string>|Especifica o namespace modelo a ser usado. O namespace é definido no arquivo .csdl durante a execução de `/mode:FullGeneration` ou `/mode:FromSSDLGeneration`. O namespace não é usado durante a execução de `/mode:EntityClassGeneration`.|
|`/entitycontainer:`\<string>|Especifica o nome que será aplicado ao elemento `<EntityContainer>` nos arquivos de mapeamento e modelos gerados.|
|`/pl[uralize]`|Aplica as regras de língua inglesa para singular e plural aos nomes de `Entity`, de `EntitySet` e de `NavigationProperty` no modelo conceitual. Essa opção executará as seguintes ações:<br /><br /> -Tornar todos `EntityType` nomes no singular.<br />-Tornar todos `EntitySet` nomes no plural.<br />-Para cada `NavigationProperty` que retornar no máximo uma entidade, verifique o nome singular.<br />-Para cada `NavigationProperty` que retorna mais de uma entidade, verifique o nome no plural.|
|`/SuppressForeignKeyProperties or /nofk`|Evita que as colunas de chave estrangeira sejam expostas como propriedades escalares em tipos de entidade no modelo conceitual.|
|`/help` ou `?`|Exibe sintaxe de comando e opções para a ferramenta.|
|`/nologo`|Suprime a notificação de direitos autorais da exibição.|
|`/targetversion:` \<string>|A versão do .NET Framework será usada para compilar o código gerado. As versões com suporte são 4 e 4.5. O padrão é 4.|

## <a name="in-this-section"></a>Nesta seção

[Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Como: Use EdmGen.exe para gerar o código da camada de objeto](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Como: Use EdmGen.exe para validar o modelo e arquivos de mapeamento](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Consulte também

- [Ferramentas de modelo de dados de entidade ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Modelo de Dados de Entidade](../../../../../docs/framework/data/adonet/entity-data-model.md)
- [CSDL, SSDL, and MSL Specifications](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md) (Especificações CSDL, SSDL e MSL)
