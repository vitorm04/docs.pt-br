---
title: "Otimização da hospedagem Web compartilhada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f423d867d4fada075800650627c94f9d09e9e7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="optimization-for-shared-web-hosting"></a>Otimização da hospedagem Web compartilhada
Se você for o administrador de um servidor que é compartilhado por vários pequenos sites da Web de hospedagem, você pode otimizar o desempenho e aumentar a capacidade do site adicionando o seguinte `gcTrimCommitOnLowMemory` definir como o `runtime` nó no arquivo ASPNET no .NET diretório:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  Essa configuração é recomendada somente para Web compartilhada cenários de hospedagem.  
  
 Como o coletor de lixo retém a memória para alocações futuras, seu espaço confirmado pode ser mais do que o que é estritamente necessário. Você pode reduzir esse espaço para acomodar vezes quando houver uma carga pesada na memória do sistema. Reduzir esse espaço confirmado melhora o desempenho e expande a capacidade de hospedar mais sites.  
  
 Quando o `gcTrimCommitOnLowMemory` configuração estiver habilitada, o coletor de lixo avalia a carga de memória do sistema e entra em um modo de corte, quando a carga atinge 90%. Ele mantém o modo de corte até que a carga em descarta 85%.  
  
 Quando as condições permitirem, o coletor de lixo pode decidir que o `gcTrimCommitOnLowMemory` configuração não ajudar o aplicativo atual e ignorá-lo.  
  
## <a name="example"></a>Exemplo  
 O fragmento XML a seguir mostra como habilitar o `gcTrimCommitOnLowMemory` configuração. As reticências indicam outras configurações que devem ser o `runtime` nó.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
