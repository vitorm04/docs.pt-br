---
title: Local de um assembly
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c736b4fe2a4bc38d4345413fa00d4cf7e5a80be7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607733"
---
# <a name="assembly-location"></a>Local de um assembly
O local de um assembly determina se o Common Language Runtime pode localizá-lo quando referenciado, bem como pode determinar se o assembly pode ser compartilhado com outros assemblies. Você pode implantar um assembly nos seguintes locais:  
  
- No diretório ou subdiretórios do aplicativo.  
  
     Esse é o local mais comum para implantar um assembly. Os subdiretórios do diretório raiz de um aplicativo podem ser baseados na linguagem ou cultura. Se um assembly tiver informações no atributo de cultura, ele deverá estar em um subdiretório no diretório do aplicativo com o nome dessa cultura.  
  
- O cache de assembly global.  
  
     Esse é um cache de código da máquina toda que é instalado sempre que o Common Language Runtime é instalado. Na maioria das vezes, se você pretende compartilhar um assembly com vários aplicativos, é preciso implantá-lo no cache de assembly global.  
  
- Em um servidor HTTP.  
  
     Um assembly implantado em um servidor HTTP deve ter um nome forte; você aponta para o assembly na seção de base de código do arquivo de configuração de aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)
- [Cache de assembly global](../../../docs/framework/app-domains/gac.md)
- [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
