---
title: "Controle de versão do .NET Core"
description: "Compreenda como o controle de versão do .NET Core funciona."
author: bleroy
ms.author: mairaw
ms.date: 08/25/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
ms.translationtype: HT
ms.sourcegitcommit: 02cfb7708959057de593506db55e4f31f5ab4fd0
ms.openlocfilehash: 48343ad8d42ad576b1975e81cd764b4ec6f5bc76
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="net-core-versioning"></a>Controle de versão do .NET Core

O .NET Core é composto por [pacotes do NuGet](../packages.md), ferramentas e estruturas que são distribuídas como uma unidade. Cada uma dessas camadas de plataforma pode ter a versão controlada separadamente, permitindo maior agilidade. Embora haja uma flexibilidade significativa de controle de versão a esse respeito, também há um desejo de controlar a versão da plataforma como uma unidade para facilitar a compreensão do produto.

Este artigo destina-se a esclarecer como o SDK do .NET Core e o tempo de execução têm a versão controlada.

Há muitas partes móveis que recebe novas versões independentemente no .NET Core. No entanto, começando com o .NET Core 2.0, há um número de versão de nível superior fácil de entender que todos entendem como sendo *a* versão do “.NET Core” como um todo. O restante deste documento investiga os detalhes do controle de versão de todas essas partes. Esses detalhes poderão ser importantes se você for um gerenciador de pacotes, por exemplo.

## <a name="versioning-details"></a>Detalhes de controle de versão

A partir do .NET Core 2.0, os downloads mostram um único número de versão em seu nome de arquivo. Os números de versão a seguir foram unificados:

* A estrutura compartilhada e o tempo de execução associado.
* O SDK do .NET Core e a CLI do .NET Core associada.
* O metapacote `Microsoft.NETCore.App`.

O uso de um único número de versão facilita para os usuários saberem qual versão do SDK instalar em seus computadores de desenvolvimento e qual deverá ser a versão correspondente da estrutura compartilhada quando for o momento de provisionar um ambiente de produção. Ao baixar um SDK ou tempo de execução, o número de versão que você verá será o mesmo.

### <a name="installers"></a>Instaladores

A partir do .NET Core 2.0, os downloads de nossos [builds diários](https://github.com/dotnet/core-setup#daily-builds) e [nossas versões](https://www.microsoft.com/net/download/core) aderem a um novo esquema de nomenclatura que é mais fácil de entender.
A interface do usuário do instalador nesses downloads também foi modificada para apresentar claramente os nomes e versões dos componentes sendo instalados. Em particular, agora os títulos mostram o mesmo número de versão que está no nome do arquivo do download.

#### <a name="file-name-format"></a>Formato de nome de arquivo

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

Aqui estão alguns exemplos desse formato:

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

O formato é legível e mostra claramente o que você está baixando, qual versão é e onde você pode usá-lo. O nome do pacote do tempo de execução inclui `runtime` e o SDK inclui `SDK`.

#### <a name="ui-string-format"></a>Formato da cadeia de caracteres da interface do usuário

Todas as descrições do site e as cadeias de caracteres da interface do usuário são mantidas simples, precisas e consistentes. A tabela a seguir mostra alguns exemplos:

| Installer | Título da janela                          | Outros conteúdos no instalador | O que é instalado                               |
| :--       | :--                                   | :--                        | :--                                             |
| SDK       | Instalador do SDK do .NET Core 2.0 (x64)     | SDK do .NET Core 2.0.4        | Ferramentas do .NET Core 2.0.4 + Tempo de execução do .NET Core 2.0.4 |
| Tempo de execução   | Instalador do Tempo de execução do .NET Core 2.0 (x64) | Tempo de execução do .NET Core 2.0.4    | Tempo de execução do .NET Core 2.0.4                         |

As versões prévias diferem apenas um pouco:

| Installer | Título da janela                                    | Outros conteúdos no instalador        | O que é instalado                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| SDK       | Instalador do SDK do .NET Core 2.0 Versão Prévia 1 (x64)     | SDK do .NET Core 2.0.0 Versão Prévia 1     | Ferramentas do .NET Core 2.0.0 Versão Prévia 1 + Tempo de execução do .NET Core 2.0.0 Versão Prévia 1 |
| Tempo de execução   | Instalador do Tempo de execução do .NET Core 2.0 Versão Prévia 1 (x64) | Tempo de execução do .NET Core 2.0.0 Versão Prévia 1 | Tempo de execução do .NET Core 2.0.0 Versão Prévia 1                                   |

Pode acontecer de uma versão do SDK conter mais de uma versão do tempo de execução. Quando isso acontece, o instalador UX tem a seguinte aparência (somente a versão do SDK é mostrada e as versões instaladas do Tempo de execução são mostradas em uma página de resumo no final do processo de instalação no Windows e no Mac):

| Installer | Título da janela                      | Outros conteúdos no instalador                                   | O que é instalado                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| SDK       | Instalador do SDK do .NET Core 2.1 (x64) | SDK do .NET Core 2.1.1 <br> Tempo de execução do .NET Core 2.1.1 <br> Tempo de execução do .NET Core 2.0.6 | Ferramentas do .NET Core 2.1.1 + Tempo de execução do .NET Core 2.1.1 + Tempo de execução do .NET Core 2.0.6 |

Também é possível que as Ferramentas do .NET Core precisem ser atualizadas, sem alterações de tempo de execução. Nesse caso, a versão do SDK é aumentada (por exemplo, para 2.1.2) e o Tempo de execução o alcança na próxima vez em que for fornecido (por exemplo, o Tempo de execução e o SDK serão fornecidos da próxima vez como 2.1.3).

### <a name="package-managers"></a>Gerenciadores de pacotes

O .NET Core pode ser distribuído por outras entidades que não a Microsoft. Em particular, os proprietários e mantenedores de pacotes de distribuição do Linux podem adicionar pacotes do .NET Core aos seus gerenciadores de pacotes. Para obter recomendações sobre como esses pacotes devem ser nomeados e ter o controle de versão realizado, consulte [.NET Core distribution packaging](../build/distribution-packaging.md) (Pacote de distribuição do .NET Core).

#### <a name="minimum-package-set"></a>Conjunto mínimo de pacote

* `dotnet-runtime-[major].[minor]`: um tempo de execução com a versão especificada (apenas a versão de patch mais recente para uma determinada combinação de principal+secundário deve estar disponível no gerenciador de pacote). As novas versões de patch atualizam o pacote, mas novas versões principais ou secundárias são pacotes separados.
 
  **Dependências**: `dotnet-host`

* `dotnet-sdk`: o SDK mais recente. `update` efetua o roll forward das versões principal, secundária e de patch.

  **Dependências**: o `dotnet-sdk-[major].[minor]` mais recente.

* `dotnet-sdk-[major].[minor]`: o SDK com a versão especificada. A versão especificada é a versão mais recente incluída das estruturas compartilhadas incluídas, para que os usuários possam relacionar facilmente um SDK a uma estrutura compartilhada. As novas versões de patch atualizam o pacote, mas novas versões principais ou secundárias são pacotes separados.

  **Dependências**: `dotnet-host`, um ou mais `dotnet-runtime-[major].[minor]` (um desses é usado pelo próprio código do SDK, os outros servem para build e execução dos usuários).

* `dotnet-host`: o host mais recente.

##### <a name="preview-versions"></a>Versões prévias

Os mantenedores do pacote podem decidir incluir versões prévias do SDK e do tempo de execução. Não inclua essas versões prévias no pacote `dotnet-sdk` sem controle de versão, mas você pode liberá-las como pacotes com controle de versão com um marcador de versão prévia adicional anexado às seções da versão principal e secundária do nome. Por exemplo, pode haver um pacote `dotnet-sdk-2.0-preview1-final`.

### <a name="docker"></a>Docker

Uma convenção de nomenclatura de marcação do Docker geral é colocar o número de versão antes do nome do componente. Essa convenção pode continuar a ser utilizada. As marcas atuais incluem somente a versão de Tempo de execução da seguinte maneira.

* 1.0.8-runtime
* 1.0.8-sdk
* 2.0.4-runtime
* 2.0.4-sdk
* 2.1.1-runtime
* 2.1.1-sdk

As marcas do SDK devem ser atualizadas para representar a versão do SDK em vez de o Tempo de execução.

Também é possível que precisemos corrigir as Ferramentas do .NET Core, mas relançar um tempo de execução existente. Nesse caso, a versão do SDK é aumentada (por exemplo, para 2.1.2) e o Tempo de execução o alcança na próxima vez em que for fornecido (por exemplo, o Tempo de execução e o SDK serão fornecidos na próxima vez como 2.1.3).

## <a name="semantic-versioning"></a>Controle de Versão Semântico

O .NET Core usa o [SemVer (Controle de Versão Semântico)](http://semver.org/), adotando o uso do controle de versão do `MAJOR.MINOR.PATCH`, usando as várias partes do número de versão para descrever o grau e o tipo de alteração.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

As partes `PRERELEASE` e `BUILDNUMBER` opcionais nunca farão parte das versões compatíveis e existem apenas em builds noturnos, compilados localmente de destinos de origem e versões prévias sem suporte.

### <a name="how-version-numbers-are-incremented"></a>Como os números de versão são incrementados?

`MAJOR` é incrementado quando:
  - Não há mais suporte para uma versão mais antiga.
  - Uma versão `MAJOR` mais nova de uma dependência existente é adotada.
  - A configuração padrão de uma sutileza de compatibilidade é alterada para "desativada".

`MINOR` é incrementado quando:
  - Uma área de superfície de API pública é adicionada.
  - Um novo comportamento é adicionado.
  - Uma versão `MINOR` mais nova de uma dependência existente é adotada.
  - Uma nova dependência é introduzida.
  
`PATCH` é incrementado quando:
  - Correções de bug são feitas.
  - O suporte para uma plataforma mais recente é adicionado.
  - Uma versão `PATCH` mais nova de uma dependência existente é adotada.
  - Qualquer outra alteração que não se enquadre em um dos casos anteriores.

Quando há várias alterações, o elemento mais alto afetado por alterações individuais é incrementado e os seguintes são redefinidos como zero. Por exemplo, quando `MAJOR` é incrementado, `MINOR` e `PATCH` são redefinidos como zero. Quando `MINOR` é incrementado, `PATCH` é redefinido como zero enquanto `MAJOR` permanece inalterado.

### <a name="preview-versions"></a>Versões prévias

As versões prévias têm um `-preview[number]-([build]|"final")` anexado à versão. Por exemplo, `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Versões de manutenção

Depois que uma versão sai, os branches de versão geralmente param de produzir builds diários e, em vez disso, iniciam a produção de builds de manutenção. As versões de manutenção têm um `-servicing-[number]` anexado à versão. Por exemplo, `2.0.1-servicing-006924`.

### <a name="lts-vs-current"></a>LTS vs. atual

Há duas linhas de versões para .NET Core: LTS (Suporte a Longo Prazo) e Atual. Isso permite que os usuários selecionem o nível de estabilidade e novos recursos que desejam, enquanto ainda têm suporte.

- LTS significa que você obtém novos recursos com menos frequência, mas tem uma plataforma mais madura. O LTS também tem um período de suporte mais longo.
- Atual significa que você obtém novos recursos e APIs com mais frequência, mas a desvantagem é que tem um período mais curto para instalar as atualizações e essas atualizações ocorrem com mais frequência. Atual também tem suporte total, mas o período de suporte é menor do que do LTS.

Uma versão "Atual" pode ser promovida a LTS.

"LTS" e "Atual" devem ser considerados como rótulos que colocamos em versões específicas para fazer uma afirmação sobre o nível de suporte associado.

Para obter mais informações, consulte a [Folha informativa sobre o ciclo de vida do suporte do .NET Core](https://www.microsoft.com/net/core/support).

## <a name="versioning-scheme-details"></a>Detalhes do esquema de controle de versão

O .NET Core é composto pelas seguintes partes:

- Um host (também conhecido como muxer): `dotnet.exe` com bibliotecas de política `hostfxr`.
- Um SDK (o conjunto de ferramentas necessário no computador do desenvolvedor, mas não na produção).
- Um tempo de execução.
- Uma implementação de estrutura compartilhada, distribuída como pacotes. Cada pacote tem controle de versão independente, especialmente para controle de versão de patch.
- Opcionalmente, um conjunto de [metapacotes](../packages.md) que fazem referência a pacotes refinados como uma unidade com controle de versão. Os metapacotes podem ter controle de versão separado dos pacotes.

O .NET Core também inclui um conjunto de estruturas de destino (por exemplo, `netstandard` ou `netcoreapp`) que representa um conjunto de APIs de cada vez maior, conforme os números de versão são incrementados.

### <a name="net-standard"></a>.NET Standard

O .NET Standard está usando um esquema de controle de versão `MAJOR.MINOR`. O nível `PATCH` não é útil para .NET Standard porque ele expressa um conjunto de contratos que são iterados com menos frequência e não apresenta os mesmos requisitos de controle de versão de uma implementação real.

Não há nenhum acoplamento real entre as versões do .NET padrão e do .NET Core: o .NET Core 2.0 implementa o .NET Standard 2.0, mas não há garantia de que as versões futuras do .NET Core serão mapeadas para a mesma versão do .NET Standard. O .NET Core pode fornecer APIs que não são definidas pelo .NET Standard e, assim, podem fornecer novas versões sem a necessidade de um novo .NET Standard. O .NET Standard também é um conceito que se aplica a outros destinos, como o .NET Framework ou Mono, mesmo que seu início tenha coincidido com om do .NET Core.

### <a name="packages"></a>Pacotes

Pacotes de biblioteca evoluem e mudam de versão independentemente. Os pacotes que apresentam sobreposição em relação aos assemblies System.\* do .NET Framework normalmente usam versões 4.x, alinhando-se ao controle de versão do .NET Framework 4.x (uma opção histórica). Pacotes que não se sobrepõem às bibliotecas do .NET Framework (por exemplo, [`System.Reflection.Metadata`](https://www.nuget.org/packages/System.Reflection.Metadata)) normalmente começam em 1.0 e aumentam a partir daí.

Os pacotes descritos por [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) são tratados de forma especial por estarem na base da plataforma.

Pacotes `NETStandard.Library` normalmente têm controle de versão como um conjunto, visto que eles têm dependências de nível de implementação entre eles.

### <a name="metapackages"></a>Metapacotes

O controle de versão para metapacotes do .NET Core baseia-se na versão do .NET Core do qual eles fazem parte.

Por exemplo, os metapacotes no .NET Core 2.1.3 devem ter 2.1 como seus números de versão `MAJOR` e `MINOR`.

A versão de patch para o metapacote é incrementada toda vez que qualquer pacote referenciado é atualizado. As versões de patch não incluem uma versão de estrutura atualizada. Como resultado, os metapacotes não são estritamente em conformidade com SemVer, pois seu esquema de controle de versão não representa o nível de alteração nos pacotes subjacentes, mas principalmente no nível de API. 

No momento, há dois metapacotes principais para o .NET Core:

**Microsoft.NETCore.App**

- v1.0 a partir do .NET Core 1.0 (essas versões coincidem).
- É mapeado para a estrutura `netcoreapp`.
- Descreve os pacotes na distribuição do .NET Core.

Observação: [`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) é outro metapacote do .NET Core existente para habilitar a compatibilidade com a implementação pré .NET Standard do .NET. Ele não é mapeado para uma determinada estrutura, por isso as versões funcionam como um pacote.

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) descreve as bibliotecas que fazem parte do [.NET Standard](../../standard/library.md). Aplica-se a todas as implementações do .NET compatíveis com o .NET Standard, como .NET Framework, .NET Core e Mono.

### <a name="target-frameworks"></a>Frameworks de destino

As versões de estruturas de destino são atualizadas quando novas APIs são adicionadas. Elas não têm conceito de versão de patch, visto que representam a forma da API e não as questões de implementação. O controle de versão principal e secundário segue as regras de SemVer especificadas anteriormente e coincide com os números `MAJOR` e `MINOR` das distribuições do .NET Core que os implementam.

## <a name="versioning-in-practice"></a>Controle de versão na prática

Quando você baixa o .NET Core, o nome do arquivo baixado contém a versão, por exemplo, `dotnet-sdk-2.0.4-win10-x64.exe`.

Há confirmações e solicitações de pull em repositórios do .NET Core no GitHub diariamente, resultando em novos builds de muitas bibliotecas. Não é viável criar novas versões públicas do .NET Core para cada alteração. Em vez disso, as alterações são agregadas por um período indeterminado (por exemplo, semanas ou meses) antes de criar uma nova versão estável pública do .NET Core.

Uma nova versão do .NET Core pode significar várias coisas:

- Novas versões de pacotes e metapacotes.
- Novas versões das várias estruturas, considerando a adição de novas APIs.
- Nova versão da distribuição do .NET Core.

### <a name="shipping-a-patch-release"></a>Enviando uma versão de patch

Após o fornecimento de uma versão principal do .NET Core, como a versão 2.0.0, são feitas alterações de nível de patch nas bibliotecas .NET Core para corrigir bugs e melhorar o desempenho e a confiabilidade. Isso significa que não foi introduzida nenhuma API. Os vários metapacotes são atualizados para referenciar os pacotes de biblioteca atualizados do .NET Core. Os metapacotes têm o controle de versão como atualizações de patch (`MAJOR.MINOR.PATCH`). As estruturas de destino nunca são atualizadas como parte das versões do patch. Uma nova distribuição do .NET Core é lançada com um número de versão correspondente ao metapacote `Microsoft.NETCore.App`.

### <a name="shipping-a-minor-release"></a>Enviando uma versão secundária

Após o fornecimento de uma versão do .NET Core com um número de versão `MAJOR` incrementado, novas APIs são adicionadas às bibliotecas do .NET Core para habilitar novos cenários. Os vários metapacotes são atualizados para referenciar os pacotes de biblioteca atualizados do .NET Core. Os metapacotes têm o controle de versão como atualizações de patch com os números de versão `MAJOR` e `MINOR` correspondendo à nova versão de estrutura. Novos nomes de estrutura de destino com a nova versão `MAJOR.MINOR` são adicionados para descrever as novas APIs (por exemplo, `netcoreapp2.1`). Uma nova distribuição .NET Core é lançada com um número de versão correspondente ao metapacote `Microsoft.NETCore.App`.

### <a name="shipping-a-major-release"></a>Enviando uma versão principal

Sempre que uma nova versão principal do .NET Core é fornecida, o número de versão do `MAJOR` é aumentado e o número de versão `MINOR` é redefinido como zero. A nova versão principal contém pelo menos todas as APIs que foram adicionadas por versões secundárias após a versão principal anterior. Uma nova versão principal deve habilitar novos cenários importantes e também pode remover o suporte para uma plataforma mais antiga.

Os vários metapacotes são atualizados para referenciar os pacotes de biblioteca atualizados do .NET Core. O metapacote [`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App) e a estrutura de destino `netcore` têm o controle de versão como uma atualização importante correspondente ao número de versão `MAJOR` da nova versão.

## <a name="see-also"></a>Consulte também
[Frameworks de destino](../../standard/frameworks.md)   
[.NET Core distribution packaging](../build/distribution-packaging.md)  (Pacote de distribuição do .NET Core)  
[Folha informativa sobre o ciclo de vida do suporte do .NET Core](https://www.microsoft.com/net/core/support)   
[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3) (Associação de versão do .NET Core 2+)   

