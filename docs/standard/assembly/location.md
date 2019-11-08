---
title: Localização do assembly
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733130"
---
# <a name="assembly-location"></a>Localização do assembly
O local de um assembly determina se o Common Language Runtime pode localizá-lo quando referenciado, bem como pode determinar se o assembly pode ser compartilhado com outros assemblies. Você pode implantar um assembly nos seguintes locais:

- No diretório ou subdiretórios do aplicativo.

     Esse é o local mais comum para implantar um assembly. Os subdiretórios do diretório raiz de um aplicativo podem ser baseados na linguagem ou cultura. Se um assembly tiver informações no atributo de cultura, ele deverá estar em um subdiretório no diretório do aplicativo com o nome dessa cultura.

- O cache de assembly global.

     Esse é um cache de código da máquina toda que é instalado sempre que o Common Language Runtime é instalado. Na maioria das vezes, se você pretende compartilhar um assembly com vários aplicativos, é preciso implantá-lo no cache de assembly global.

- Em um servidor HTTP.

     Um assembly implantado em um servidor HTTP deve ter um nome forte; você aponta para o assembly na seção de base de código do arquivo de configuração de aplicativo.

## <a name="see-also"></a>Consulte também

- [Criar assemblies](create.md)
- [Cache de assembly global](../../framework/app-domains/gac.md)
- [Como o runtime localiza assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md)
