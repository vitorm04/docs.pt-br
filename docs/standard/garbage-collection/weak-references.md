---
title: "Referências fracas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a>Referências fracas
O coletor de lixo não pode coletar um objeto em uso por um aplicativo enquanto o código do aplicativo pode acessar esse objeto. O aplicativo tem uma referência forte para o objeto.  
  
 Uma referência fraca permite que o coletor de lixo colete o objeto enquanto ainda permite que o aplicativo o acesse. Uma referência fraca é válida somente durante o período indeterminado até que o objeto seja coletado quando não há nenhuma referência forte. Quando você usa uma referência fraca, o aplicativo ainda pode obter uma referência forte para o objeto, o que impede que ele seja coletado. No entanto, sempre há o risco de o coletor de lixo obter o objeto primeiro antes de uma referência forte ser restabelecida.  
  
 As referências fracas são úteis para objetos que usam muita memória, mas podem ser facilmente recriados se forem recuperados pela coleta de lixo.  
  
 Suponha que uma exibição de árvore em um aplicativo Windows Forms exibe uma opção complexa hierárquica das opções para o usuário. Se os dados subjacentes forem grandes, manter a árvore na memória é ineficiente quando o usuário está envolvido com outra coisa no aplicativo.  
  
 Quando o usuário alterna imediatamente para outra parte do aplicativo, você pode usar o <xref:System.WeakReference> classe para criar uma referência fraca a árvore e destruir todas as referências de alta seguras. Quando o usuário alterna de volta para a árvore, o aplicativo tenta obter uma referência forte para a árvore e, se tiver êxito, evita a reconstrução da árvore.  
  
 Para estabelecer uma referência fraca com um objeto, você cria um <xref:System.WeakReference> usando a instância do objeto a ser rastreada. Você definir o <xref:System.WeakReference.Target%2A> propriedade para esse objeto e o conjunto original de referência para o objeto a ser `null`. Para obter um exemplo de código, consulte <xref:System.WeakReference> na biblioteca de classes.  
  
## <a name="short-and-long-weak-references"></a>Referências fracas curtas e longas  
 Você pode criar uma referência fraca curta ou uma referência fraca longa:  
  
-   Abreviado  
  
     O destino de uma referência fraca curta se torna `null` quando o objeto é recuperado pela coleta de lixo. A referência fraca é um objeto gerenciado e está sujeita à coleta de lixo assim como qualquer outro objeto gerenciado.  Uma referência fraca curta é o construtor padrão para <xref:System.WeakReference>.  
  
-   Long  
  
     Uma referência fraca longa é mantida após o objeto <xref:System.Object.Finalize%2A> método foi chamado. Isso permite que o objeto seja recriado, mas o estado do objeto permanece imprevisível. Para usar uma referência de tempo, especifique `true` no <xref:System.WeakReference> construtor.  
  
     Se o tipo de objeto não tem um <xref:System.Object.Finalize%2A> aplica-se do método, a funcionalidade de referência fraca curto e a referência fraca é válida somente até que o destino é coletado, que podem ocorrer a qualquer momento após o finalizador é executado.  
  
 Para estabelecer uma referência forte e usar o objeto novamente, converter o <xref:System.WeakReference.Target%2A> propriedade de um <xref:System.WeakReference> para o tipo do objeto. Se o <xref:System.WeakReference.Target%2A> propriedade retorna `null`, o objeto foi coletado; caso contrário, você pode continuar a usar o objeto porque o aplicativo foi recuperado uma referência forte para ele.  
  
## <a name="guidelines-for-using-weak-references"></a>Diretrizes para usar referências fracas  
 Use referências fracas longas somente quando necessário, uma vez que o estado do objeto é imprevisível após a finalização.  
  
 Evite usar referências fracas para objetos pequenos, pois o ponteiro em si pode ser tão grande quanto ou maior.  
  
 Evite usar referências fracas como uma solução automática para problemas de gerenciamento de memória. Em vez disso, desenvolva uma política de cache efetiva para lidar com os objetos do seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
