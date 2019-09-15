---
title: Local do assembly
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6427f7d005c43ef9e83387e865f71009b683a7c4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973176"
---
# <a name="assembly-location"></a>Local do assembly
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
- [Como o tempo de execução localiza assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programa com assemblies](program.md)
