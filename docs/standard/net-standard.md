---
title: .NET Standard
description: Saiba mais sobre o .NET Standard, suas versões e as implementações de .NET que dão suporte a ele.
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.technology: dotnet-standard
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 832efe566aaab1e0add687cdb474bacdf5b5d829
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590875"
---
# <a name="net-standard"></a>.NET Standard

O [.NET Standard](https://github.com/dotnet/standard) é uma especificação formal de APIs do .NET que devem estar disponíveis em todas as implementações do .NET. A motivação por trás do .NET Standard é estabelecer maior uniformidade no ecossistema do .NET. A [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) continua a estabelecer a uniformidade de comportamento da implementação do .NET, mas não há especificação semelhante para as BCLs (Bibliotecas de Classe Base) para implementações da biblioteca do .NET. 

O .NET Standard permite os seguintes principais cenários: 

- Define um conjunto uniforme de APIs de BCL para todas as implementações do .NET a serem implementadas, independentemente da carga de trabalho.
- Permite que os desenvolvedores criem bibliotecas portáteis, utilizáveis entre implementações do .NET, usando esse mesmo conjunto de APIs.
- Reduz ou até elimina a compilação condicional de origem compartilhada em razão das APIs do .NET, apenas para APIs do sistema operacional.

As diversas implementações do .NET se destinam a versões específicas do .NET Standard. Cada versão de implementação do .NET anuncia a versão mais alta do .NET Standard a qual ela dá suporte, uma afirmação que significa que também há suporte para versões anteriores. Por exemplo, o .NET Framework 4.6 implementa o .NET Standard 1.3, o que significa que ele expõe todas as APIs definidas nas versões 1.0 a 1.3 do .NET Standard. Da mesma forma, o .NET Framework 4.6.1 implementa o .NET Standard 1.4, enquanto o .NET Core 1.0 implementa o .NET Standard 1.6.

## <a name="net-implementation-support"></a>Suporte à implementação do .NET

A tabela a seguir lista todas as versões do .NET Standard e as plataformas com suporte:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

Para localizar a versão mais recente do .NET Standard para a qual você pode direcionar, faça o seguinte:
1. Localize a linha que indica a implementação do .NET na qual você deseja executar.
2. Localize a coluna nessa linha que indica sua versão, da direita para a esquerda.
3. O cabeçalho da coluna indica a versão do .NET Standard a qual seu destino oferece suporte (e as versões de .NET Standard inferiores também darão suporte).
4. Repita esse processo para cada plataforma de destino. Se você tiver mais de uma plataforma de destino, escolha a versão menos recente entre elas. Por exemplo, se você quiser executar no .NET Framework 4.5 e no .NET Core 1.0, a versão mais recente do .NET Standard que você pode usar é o .NET Standard 1.1.

### <a name="which-net-standard-version-to-target"></a>Para qual versão do .NET Standard direcionar

Ao escolher uma versão do .NET Standard, você deve considerar a seguinte compensação:

- Quanto mais recente a versão, mais APIs estarão disponíveis para você.
- Quanto menos recente a versão, mais plataformas a implementarão.

Em geral, recomendamos que você direcione para a versão *menos recente* possível do .NET Standard. Portanto, depois de localizar a versão mais recente do .NET Standard para a qual você pode direcionar, execute estas etapas:
1. Direcione para a próxima versão menos recente do .NET Standard e compile seu projeto.
2. Se seu projeto for compilado com êxito, repita a etapa 1. Caso contrário, redirecione para a próxima versão mais recente, e essa será a versão que você deve usar.

### <a name="net-standard-versioning-rules"></a>Regras de controle de versão do .NET Standard

Há duas regras principais de controle de versão:

- Aditivo: as versões do .NET Standard são círculos logicamente concêntricos: versões mais recentes incorporam todas as APIs das versões anteriores. Não há alterações significativas entre as versões.
- Imutável. Após o envio, as versões do .NET Standard são congeladas. As novas APIs ficarão disponíveis primeiro em implementações específicas do .NET, como .NET Core. Se a equipe de revisão do .NET Standard acreditar que as novas APIs devem ser disponibilizadas em qualquer lugar, elas serão adicionadas em uma nova versão do .NET Standard.

## <a name="comparison-to-portable-class-libraries"></a>Comparação com bibliotecas de classes portáteis

O .NET Standard é o substituto das [PCLs (Bibliotecas de classe portáteis)](./cross-platform/cross-platform-development-with-the-portable-class-library.md). O .NET Standard aprimora a experiência de criar bibliotecas portáteis, selecionando um BCL padrão e estabelecendo maior uniformidade entre as implementações do .NET como resultado. Uma biblioteca direcionada ao .NET Standard é uma PCL ou uma “PCL baseada no .NET Standard”. PCLs existentes são "PCLs baseadas em perfil".

Os perfis do .NET Standard e da PCL foram criados para finalidades semelhantes, mas também diferem de maneiras básicas.

Semelhanças:

- Define as APIs que podem ser usados para compartilhamento de código binário.

Diferenças:

- O .NET Standard é um conjunto estruturado de APIs, enquanto os perfis de PCL são definidos por interseções de plataformas existentes.
- O .NET Standard tem versões lineares, ao passo que os perfis de PCL não.
- Os perfis de PCL representam plataformas da Microsoft enquanto o .NET Standard é independente de plataforma.

## <a name="specification"></a>Especificação

A especificação do .NET Standard é um conjunto padronizado de APIs. A especificação é mantida por implementações do .NET, especificamente Microsoft (inclui o .NET Framework, .NET Core e Mono) e Unity. Um processo de comentários público é usado como parte do estabelecimento de novas versões do .NET Standard por meio do [GitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Artefatos oficiais

A especificação oficial é um conjunto de arquivos .cs que definem as APIs que fazem parte do padrão. O [diretório ref](https://github.com/dotnet/standard/tree/master/netstandard/ref) em [dotnet/standard repository](https://github.com/dotnet/standard) define as APIs do .NET Standard.

O metapacote [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) ([de origem](https://github.com/dotnet/standard/blob/master/netstandard/pkg/NETStandard.Library.dependencies.props)) descreve o conjunto de bibliotecas que define (parcialmente) uma ou mais versões do .NET Standard.

Um componente específico, como System. Runtime, descreve:

- Parte do .NET Standard (apenas seu escopo).
- Várias versões do .NET Standard, para esse escopo.

Artefatos derivados são fornecidos para habilitar leitura mais conveniente e permitir determinados cenários do desenvolvedor (por exemplo, usando um compilador).

- [Lista de APIs em markdown](https://github.com/dotnet/standard/tree/master/docs/versions)
- Assemblies de referência, distribuídos como [pacotes NuGet](../core/packages.md) e referenciados pelo metapacote [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/).

### <a name="package-representation"></a>Representação de pacote

O meio de distribuição principal dos assemblies de referência do .NET Standard são os [pacotes NuGet](../core/packages.md). As implementações serão entregues de várias formas, apropriadas para cada implementação do .NET.

Pacotes NuGet são direcionados a uma ou mais [estruturas](frameworks.md). Os pacotes do .NET Standard são direcionados à estrutura do ".NET Standard". Você pode direcionar o .NET Standard Framework usando o `netstandard` [ TFM compacto](frameworks.md) (por exemplo, `netstandard1.4`). Bibliotecas destinadas à execução em vários tempos de execução devem ter essa estrutura como destino. 

O metapacote `NETStandard.Library` faz referência ao conjunto completo de pacotes NuGet que definem o .NET Standard.  A maneira mais comum de apontar `netstandard` é fazer referência a esse metapacote. Ele descreve e fornece acesso às ~40 bibliotecas .NET e APIs associadas, que definem a .NET Standard. Você pode referenciar pacotes adicionais destinados a `netstandard` para obter acesso a APIs adicionais. 

### <a name="versioning"></a>Controle de versão

A especificação não é única, mas um conjunto de versões de APIs de crescimento incremental e linear. A primeira versão do padrão estabelece um conjunto de linhas de base de APIs. As versões subsequentes adicionam APIs e herdam APIs definidas por versões anteriores. Não há nenhuma provisão estabelecido para remoção de APIs do padrão.

O .NET Standard não é específico a nenhuma implementação do .NET, nem corresponde ao esquema de controle de versão de nenhum desses tempos de execução.

APIs adicionadas a qualquer implementação (por exemplo, .NET Framework, .NET Core e Mono) podem ser consideradas como candidatas a serem adicionadas à especificação, especialmente se forem consideradas fundamentais por natureza. As novas [versões do .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) são criadas com base em versões de implementação do .NET, permitindo que você destine a novas APIs de uma PCL do .NET Standard. Os mecanismos de controle de versão são descritos mais detalhadamente em [Controle de versão do .NET Core](../core/versions/index.md).

O controle de versão do .NET Standard é importante para uso. Com uma versão do .NET Standard você pode usar bibliotecas direcionadas a essa mesma versão ou inferior. A abordagem a seguir descreve o fluxo de trabalho para uso de PCLs do .NET Standard, específico ao direcionamento do .NET Standard.

- Selecione uma versão do .NET Standard a ser usada para a PCL.
- Use bibliotecas que dependem da mesma versão do .NET Standard ou inferior.
- Se você encontrar uma biblioteca que depende de uma versão mais recente do .NET Standard, deverá adotar essa mesma versão ou decidir não usar essa biblioteca.

### <a name="pcl-compatibility"></a>Compatibilidade com PCL

O .NET Standard é compatível com um subconjunto de perfis de PCL. O .NET Standard 1.0, 1.1 e 1.2 se sobrepõem, cada um, com um conjunto de perfis de PCL. Essa sobreposição foi criada por dois motivos:

- Habilite PCLs baseadas no .NET Standard para referenciar PCLs baseadas em perfil.
- Permita que PCLs baseadas em perfil sejam empacotadas como PCLs baseadas no .NET Standard.

Compatibilidade de PCL baseada em perfil é fornecida pelo pacote NuGet. [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility). Essa dependência é necessária ao referenciar pacotes NuGet que contêm PCLs baseadas em perfil.

PCLs baseadas em perfil e empacotadas como `netstandard` são mais fáceis de serem consumidas do que PCLs baseadas em perfil tipicamente empacotadas. `netstandard` o empacotamento é compatível com os usuários existentes.

Você pode ver o conjunto de perfis PCL que são compatíveis com o .NET Standard: 

| Perfil do PCL | .NET Standard | Plataformas PCL
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4.5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profile44   | 1.2           | .NET Framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | .NET Framework 4.5, Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile111  | 1.1           | .NET Framework 4.5, Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile259  | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8


## <a name="targeting-net-standard"></a>Direcionamento do .NET Standard

Você pode [criar .NET Standard Libraries](../core/tutorials/libraries.md) usando uma combinação de `netstandard` estrutura e metapacote NETStandard.Library. Você pode ver exemplos de [direcionamento do .NET Standard com as ferramentas do .NET Core](../core/packages.md).

## <a name="see-also"></a>Consulte também
[Versões do .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md)
