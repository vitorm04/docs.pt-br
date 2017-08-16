---
title: Bibliotecas de Classe do .NET
description: Bibliotecas de Classe do .NET
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 028fd4961c97e31ea9f213b832c723b2ce2cf27c
ms.lasthandoff: 03/03/2017

---

# <a name="net-class-libraries"></a>Bibliotecas de Classe do .NET

As bibliotecas de classe são o conceito de [biblioteca compartilhada](http://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) para .NET. Elas permitem que você componentize funcionalidades úteis em módulos que podem ser usados por vários aplicativos. Elas também podem ser usadas como um meio de carregar a funcionalidade não necessária ou não conhecida na inicialização do aplicativo. Bibliotecas de classe são descritas usando o [formato de arquivo do Assembly .NET](assembly-format.md).

Há três tipos de bibliotecas de classes que você pode usar:

*   Bibliotecas de classe **específicas da plataforma** têm acesso a todas as APIs em uma determinada plataforma (por exemplo, .NET Framework, Xamarin iOS), mas só podem ser usadas por aplicativos e bibliotecas que direcionam essa plataforma.
*   Bibliotecas de classe **portáteis** têm acesso a um subconjunto de APIs e podem ser usadas por aplicativos e bibliotecas voltados para várias plataformas.
*   Bibliotecas de classe **.NET Core** são uma fusão do conceito de biblioteca portátil e específica da plataforma em um único modelo que fornece o melhor dos dois mundos.

## <a name="platform-specific-class-libraries"></a>Bibliotecas de classes específicas da plataforma

Bibliotecas específicas da plataforma estão associadas a uma única plataforma .NET (por exemplo, .NET Framework no Windows) e, portanto, podem levar a dependências significativas em um ambiente de execução conhecido. Esse ambiente exporá um conjunto conhecido de APIs (.NET e APIs de SO) e manterá e exporá o estado esperado (por exemplo, o Registro do Windows).

Os desenvolvedores que criam bibliotecas específicas de plataforma podem aproveitar ao máximo a plataforma subjacente. As bibliotecas só serão executadas na plataforma específica, fazendo verificações de plataforma ou outras formas de código condicional desnecessários (módulo de códigos de fornecimento únicos para várias plataformas).

Bibliotecas específicas da plataforma são o tipo de biblioteca de classes principal para o .NET Framework. Mesmo que outras plataformas .NET tenham surgido, as bibliotecas específicas da plataforma permaneceram o tipo de biblioteca dominante.

## <a name="portable-class-libraries"></a>Bibliotecas de Classes Portáteis

Há suporte para bibliotecas portáteis em várias plataformas .NET. Elas ainda podem assumir dependências em um ambiente de execução conhecido, no entanto, o ambiente é sintético e é gerado pela interseção de um conjunto de plataformas .NET concretas. Isso significa que suposições de plataforma e APIs expostas são um subconjunto que estaria disponível em uma biblioteca específica da plataforma.

Você escolhe uma configuração de plataforma ao criar uma biblioteca portátil. Esses são os conjuntos de plataformas que você precisa dar suporte (por exemplo, .NET Framework 4.5+, Windows Phone 8.0+). Quanto mais plataformas você escolher dar suporte, menos suposições de plataforma terá que fazer e menor será o denominador comum. Essa característica pode ser confusa a princípio, já que as pessoas geralmente pensam que "mais é melhor", mas descobrem que mais plataformas com suporte resultam em menos APIs disponíveis.

Muitos desenvolvedores de biblioteca mudam de produzir várias bibliotecas específicas de plataforma de uma origem (usando as diretivas de compilação condicional) para bibliotecas portáteis. Há [várias abordagens](http://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) para acessar a funcionalidade específica da plataforma nas bibliotecas portáteis com a técnica [bait-and-switch](http://log.paulbetts.org/the-bait-and-switch-pcl-trick/), a mais amplamente aceita neste momento.

### <a name="net-core-class-libraries"></a>Bibliotecas de Classes do .NET Core

As bibliotecas do .NET Core são uma substituição dos conceitos de bibliotecas específicas da plataforma e portáteis. Elas são específicas da plataforma no sentido de que expõem toda a funcionalidade da plataforma subjacente (sem plataformas sintéticas ou interseções de plataforma). Elas são portáteis no sentido de que funcionam em todas as plataformas de suporte.

O .NET Core expõe um conjunto _contratos_ de biblioteca. Plataformas .NET devem dar suporte a cada contrato completo ou não. Cada plataforma, portanto, dá suporte a um conjunto de contratos do .NET Core. O resultado é que há suporte para cada biblioteca de classes do .NET Core nas plataformas que dão suporte às dependências de contrato.

Os contratos do .NET Core não expõem toda a funcionalidade do .NET Framework (nem são que uma meta), no entanto, eles expõem mais APIs que as Bibliotecas de Classe Portáteis. Mais APIs serão adicionadas ao longo do tempo.

As seguintes plataformas dão suporte a bibliotecas de classes do .NET Core:

*   .NET Core
*   ASP.NET Core
*   .NET Framework 4.5+
*   Aplicativos da Windows Store
*   Windows Phone 8+

### <a name="mono-class-libraries"></a>Bibliotecas de Classe do Mono

Há suporte para as bibliotecas de classe no Mono, incluindo os três tipos de bibliotecas descritas acima. Mono era geralmente visto (corretamente) como uma implementação de plataforma cruzada do Microsoft .NET Framework. Em parte, isso acontecia porque bibliotecas do .NET Framework específicas da plataforma podiam ser executadas no tempo de execução do Mono sem modificação ou recompilação. Essa característica estava em vigor antes da criação de bibliotecas de classes portáteis, portanto, era uma opção óbvia para habilitar a portabilidade binária entre o .NET Framework e o Mono (embora ele funcionasse apenas em uma direção).

