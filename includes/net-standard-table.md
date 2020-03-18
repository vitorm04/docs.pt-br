---
ms.openlocfilehash: 9e95db8a1530fabd30b5344c87728b9210c0ad69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802841"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2,0                 | 3.0 |
| .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | N/A<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5.16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| Plataforma Universal do Windows | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | TBD |

<sup>1 As versões listadas para .NET Framework aplicam-se ao .NET Core 2.0 SDK e versões posteriores da ferramenta. As versões mais antigas usaram um mapeamento diferente para .NET Standard 1.5 ou superior. Você pode [baixar ferramentas para ferramentas .NET Core para visual Studio 2015](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) se você não puder atualizar para o Visual Studio 2017 ou uma versão posterior.</sup>

<sup>2 As versões listadas aqui representam as regras que o NuGet usa para determinar se uma determinada biblioteca .NET Standard é aplicável. Embora o NuGet considere o .NET Framework 4.6.1 como suporte ao .NET Standard 1.5 a 2.0, existem vários problemas com o consumo de bibliotecas .NET Standard que foram construídas para essas versões a partir de projetos .NET Framework 4.6.1. Para projetos .NET Framework que precisam usar tais bibliotecas, recomendamos que você atualize o projeto para segmentar o .NET Framework 4.7.2 ou superior.</sup>

<sup>3 .NET Framework não suportará versões .NET Standard 2.1 ou posteriores. Para obter mais detalhes, consulte o [anúncio do .NET Standard 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/).</sup>

- As colunas representam versões do .NET Standard. Cada célula de cabeçalho é um link para um documento que mostra quais APIs foram adicionadas a essa versão do .NET Standard.
- As linhas representam as diferentes implementações do .NET.
- O número de versão em cada célula indica a versão *mínima* da implementação de que você precisará para direcionar essa versão do .NET Standard.
- Para obter uma tabela interativa, consulte [Versões do .NET Standard](https://dotnet.microsoft.com/platform/dotnet-standard#versions).

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md
