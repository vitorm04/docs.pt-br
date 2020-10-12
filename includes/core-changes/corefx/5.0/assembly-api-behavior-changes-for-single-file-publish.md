---
ms.openlocfilehash: 0d6847b7a937094f36efae70ae450cc37824221d
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955545"
---
### <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a>Alterações de comportamento da API relacionadas ao assembly para o formato de publicação de arquivo único

Várias APIs relacionadas ao local do arquivo de um assembly têm alterações de comportamento quando são invocadas em um formato de publicação de arquivo único.

#### <a name="change-description"></a>Descrição das alterações

Na publicação de arquivo único para .NET 5,0 e versões posteriores, os assemblies agrupados são carregados da memória, em vez de serem extraídos em disco. Para aplicativos publicados de arquivo único, isso significa que determinadas APIs relacionadas ao local retornam valores diferentes no .NET 5,0 e posteriores do que nas versões anteriores do .NET. As alterações são as seguintes:

| API | Versões anteriores | .NET 5,0 e posterior |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | Retorna o caminho do arquivo DLL extraído | Retorna uma cadeia de caracteres vazia para assemblies agrupados |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | Retorna o caminho do arquivo DLL extraído | Gera uma exceção para assemblies agrupados |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | Retorna `null` para assemblies agrupados | Gera uma exceção para assemblies agrupados |
| `Environment.GetCommandLineArgs()[0]` | Valor é o nome da DLL do ponto de entrada | Value é o nome do executável do host |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | O valor é o diretório de extração temporário | O valor é o diretório recipiente do executável do host |

#### <a name="version-introduced"></a>Versão introduzida

5.0

#### <a name="recommended-action"></a>Ação recomendada

Evite dependências no local do arquivo de assemblies ao publicar como um único arquivo.

#### <a name="category"></a>Categoria

- Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
