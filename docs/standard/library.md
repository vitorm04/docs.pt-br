---
title: .NET Standard Library
description: .NET Standard Library
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
translationtype: Human Translation
ms.sourcegitcommit: f9ffbb2e300df2080276096095a7269736260ba1
ms.openlocfilehash: d56ddc264d861081f0b808711cccd489a374c0b8

---

# <a name="net-standard-library"></a>.NET Standard Library

O .NET Standard Library é uma especificação formal de APIs do .NET que devem estar disponíveis em todos os tempos de execução do .NET. A motivação por trás do Standard Library é estabelecer maior uniformidade no ecossistema do .NET. [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) continua a estabelecer a uniformidade de comportamento de tempo de execução do .NET, mas não há especificação semelhante para a BCL (Biblioteca de Classes Base) para implementações da biblioteca do .NET. 

O .NET Standard Library permite os seguintes principais cenários: 

- Define um conjunto uniforme de APIs de BCL para implementação em todas as plataformas do .NET, independentemente da carga de trabalho.
- Permite que os desenvolvedores criem bibliotecas portáteis, utilizáveis em tempos de execução do .NET, usando esse mesmo conjunto de APIs.
- Reduz e elimina a compilação condicional de origem compartilhada em razão das APIs do .NET, apenas para APIs do sistema operacional.

Os diversos tempos de execução do .NET implementam versões específicas do .NET Standard Library. Cada versão de tempo de execução do .NET anuncia a versão mais alta do .NET Standard que ela dá suporte, uma instrução que significa que também há suporte para versões anteriores. Por exemplo, o .NET Framework 4.6 implementa o .NET Standard Library 1.3, que significa que ele expõe todas as APIs definidas nas versões 1.0 a 1.3 do .NET Standard Library. Da mesma forma, o .NET Framework 4.6.2 implementa o .NET Standard Library 1.5, enquanto o .NET Core 1.0 implementa o .NET Standard Library 1.6.

## <a name="net-platforms-support"></a>Suporte a plataformas .NET

Você pode ver o conjunto completo de tempos de execução do .NET que oferecem suporte ao .NET Standard Library.

| Nome da plataforma | Alias |  |  |  |  |  | | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 | 2.0 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|vNext|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|vNext|4.6.1|
|Plataformas Mono/Xamarin||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|vNext|
|Plataforma Universal do Windows|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|&rarr;|&rarr;|vNext|
|Windows|win|&rarr;|8.0|8.1||||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1||||||
|Windows Phone Silverlight|wp|8.0||||||||

## <a name="comparison-to-portable-class-libraries"></a>Comparação com bibliotecas de classes portáteis

O .NET Standard Library pode ser pensado como a próxima geração de [PCLs (Bibliotecas de Classes Portáteis)](https://msdn.microsoft.com/library/gg597391.aspx). O .NET Standard Library aprimora a experiência de criar bibliotecas portáteis, coletando um BCL padrão e estabelecendo maior uniformidade nos tempos de execução do .NET como resultado. Uma biblioteca direcionada ao .NET Standard Library é uma PCL ou uma “PCL baseada no .NET Standard”. PCLs existentes são "PCLs baseadas em perfil".

Os perfis do .NET Standard Library e da PCL foram criados para finalidades semelhantes, mas também diferem de maneiras básicas.

Semelhanças:

- Define as APIs que podem ser usados para compartilhamento de código binário.

Diferenças:

- O .NET Standard Library é um conjunto estruturado de APIs, enquanto os perfis de PCL são definidos por interseções de plataformas existentes.
- O .NET Standard Library tem versões lineares, ao passo que os perfis de PCL não.
- Os perfis de PCL representam plataformas da Microsoft enquanto o .NET Standard Library é independente de plataforma.

## <a name="specification"></a>Especificação

A especificação do .NET Standard Library é um conjunto padronizado de APIs. A especificação é mantida por implementações de tempo de execução do .NET, especificamente o Microsoft (inclui o .NET Framework, .NET Core e Mono) e o Unity. Um processo de comentários público é usado como parte do estabelecimento de novas versões do .NET Standard Library.

### <a name="official-artifacts"></a>Artefatos oficiais

A especificação oficial é um conjunto de arquivos .cs que definem as APIs que fazem parte do padrão. O [diretório de referência](https://github.com/dotnet/corefx/tree/master/src/System.Runtime/ref) de cada [componente](https://github.com/dotnet/corefx/tree/master/src) define as APIs do .NET Standard Library. Os artefatos de referência residem no [repositório do CoreFX](https://github.com/dotnet/corefx), mas eles não são específicos do .NET Core.

O metapacote [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) ([de origem](https://github.com/dotnet/corefx/blob/master/pkg/NETStandard.Library/NETStandard.Library.packages.targets)) descreve o conjunto de bibliotecas que define (parcialmente) uma ou mais versões do .NET Standard Library.

Um componente específico, como System. Runtime, descreve:

- Parte do .NET Standard Library (apenas seu escopo).
- Várias versões do .NET Standard Library, para esse escopo.

Artefatos derivados são fornecidos para habilitar leitura mais conveniente e permitir determinados cenários do desenvolvedor (por exemplo, usando um compilador).

- Lista de APIs em markdown (TBD)
- Assemblies de referência, distribuídos como [pacotes NuGet](../core/packages.md) e referenciados pelo metapacote [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/).

### <a name="package-representation"></a>Representação de pacote

O meio de distribuição principal dos assemblies de referência do .NET Standard Library são os [pacotes NuGet](../core/packages.md). As implementações serão entregues de várias formas, apropriadas para cada tempo de execução do .NET.

Pacotes NuGet são direcionados a uma ou mais [estruturas](frameworks.md). Os pacotes do .NET Standard Library são direcionados à estrutura do ".NET Standard". Você pode direcionar o .NET Standard Framework usando o `netstandard` [ TFM compacto](frameworks.md) (por exemplo, `netstandard1.4`). Bibliotecas destinadas a execução em vários tempos de execução devem ter essa estrutura como alvo. 

O metapacote `NETStandard.Library` faz referência ao conjunto completo de pacotes NuGet que definem o .NET Standard Library.  A maneira mais comum de apontar `netstandard` é fazer referência a esse metapacote. Ele descreve e fornece acesso às ~40 bibliotecas .NET e APIs associadas, que definem a .NET Standard Library. Você pode referenciar pacotes adicionais destinados a `netstandard` para obter acesso a APIs adicionais. 

### <a name="versioning"></a>Controle de versão

A especificação não é única, mas um conjunto de versões de APIs de crescimento incremental e linear. A primeira versão do padrão estabelece um conjunto de linhas de base de APIs. As versões subsequentes adicionam APIs e herdam APIs definidas por versões anteriores. Não há nenhuma provisão estabelecido para remoção de APIs do padrão.

O .NET Standard Library não é específico a nenhum tempo de execução do .NET, nem corresponde ao esquema de controle de versão de nenhum desses tempos de execução.

APIs adicionadas a qualquer tempo de execução (por exemplo, .NET Framework, .NET Core e Mono) podem ser consideradas como candidatas a serem adicionadas à especificação, especialmente se forem consideradas fundamentais por natureza. Novas [versões do .NET Standard Library](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/net-platform-standard.md#list-of-net-corefx-apis-and-their-associated-net-platform-standard-version) são criadas com base em versões do tempo de execução do .NET, permitindo que você aponte novas APIs de uma PCL do .NET Standard. Os mecanismos de controle de versão são descritos mais detalhadamente em [Controle de versão do .NET Core](../core/versions/index.md).

O controle de versão do .NET Standard Library é importante para uso. Com uma versão do .NET Standard Library você pode usar bibliotecas direcionadas a essa mesma versão ou inferior. A abordagem a seguir descreve o fluxo de trabalho para uso de PCLs do .NET Standard Library, específico ao direcionamento do .NET Standard Library.

- Selecione uma versão do .NET Standard Library a ser usada para a PCL.
- Use bibliotecas que dependem da mesma versão do .NET Standard Library ou inferior.
- Se você encontrar uma biblioteca que depende de uma versão mais recente do .NET Standard Library, deverá adotar essa mesma versão ou decidir não usar essa biblioteca.

### <a name="pcl-compatibility"></a>Compatibilidade com PCL

O .NET Standard Library é compatível com um subconjunto de perfis de PCL. O .NET standard Library 1.0, 1.1 e 1.2 se sobrepõem, cada um, com um conjunto de perfis de PCL. Essa sobreposição foi criada por dois motivos:

- Habilite PCLs baseadas no .NET Standard para referenciar PCLs baseadas em perfil.
- Permita que PCLs baseadas em perfil sejam empacotadas como PCLs baseadas no .NET Standard.

Compatibilidade de PCL baseada em perfil é fornecida pelo pacote NuGet. [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility). Essa dependência é necessária ao referenciar pacotes NuGet que contêm PCLs baseadas em perfil.

PCLs baseadas em perfil e empacotadas como `netstandard` são mais fáceis de consumir do que PCLs baseadas em perfil empacotadas normalmente em project.json. `netstandard` o empacotamento é compatível com os usuários existentes.

Você pode ver o conjunto de perfis PCL que são compatíveis com o .NET Standard: 

| Perfil | Versão do .NET Platform Standard |
| ---------| --------------- |
| Profile7 .NET Portable Subset (.NET Framework 4.5, Windows 8) | 1.1 |
| Profile31 .NET Portable Subset (Windows 8.1, Windows Phone Silverlight 8.1)| 1.0 |
| Profile32 .NET Portable Subset (Windows 8.1, Windows Phone 8.1) | 1.2 |
| Profile44 .NET Portable Subset (.NET Framework 4.5.1, Windows 8.1) | 1.2 |
| Profile49 .NET Portable Subset (.NET Framework 4.5, Windows Phone Silverlight 8) | 1.0 |
| Profile78 .NET Portable Subset (.NET Framework 4.5, Windows 8, Windows Phone Silverlight 8) | 1.0 |
| Profile84 .NET Portable Subset (Windows Phone 8.1, Windows Phone Silverlight 8.1) | 1.0 |
| Profile111 .NET Portable Subset (.NET Framework 4.5, Windows 8, Windows Phone 8.1) | 1.1 |
| Profile151 .NET Portable Subset (.NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1) | 1.2 |
| Profile157 .NET Portable Subset (Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1) | 1.0 |
| Profile259 .NET Portable Subset (.NET Framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8) | 1.0 |

## <a name="targeting-net-standard-library"></a>Direcionamento do .NET Standard Library

Você pode [criar .NET Standard Libraries](../core/tutorials/libraries.md) usando uma combinação de `netstandard` estrutura e metapacote NETStandard.Library. Você pode ver exemplos de [direcionamento do .NET Standard Library com as ferramentas do .NET Core](../core/packages.md).



<!--HONumber=Nov16_HO3-->


