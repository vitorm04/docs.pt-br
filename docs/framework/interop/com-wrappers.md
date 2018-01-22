---
title: Wrappers COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b899ed162fa626f8c378923907f275cebf9a7db4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="com-wrappers"></a>Wrappers COM
O COM difere do modelo de objeto .NET Framework de várias maneiras importantes:  
  
-   Os clientes de objetos COM devem gerenciar o tempo de vida desses objetos; o Common Language Runtime gerencia o tempo de vida de objetos em seu ambiente.  
  
-   Os clientes de objetos COM descobrem se um serviço está disponível solicitando uma interface que fornece esse serviço e recebendo um ponteiro de interface ou não. Os clientes de objetos .NET podem obter uma descrição da funcionalidade de um objeto usando a reflexão.  
  
-   Os objetos .NET residem na memória gerenciada pelo ambiente de execução do .NET Framework. O ambiente de execução pode mover objetos na memória por motivos de desempenho e atualizar todas as referências nos objetos movidos por ele. Os clientes não gerenciados, depois de obter um ponteiro para um objeto, dependem do objeto para permanecerem no mesmo local. Esses clientes não têm nenhum mecanismo para lidar com um objeto cujo local não é fixo.  
  
 Para superar essas diferenças, o tempo de execução fornece classes wrapper para fazer com que os clientes gerenciados e não gerenciados acreditem que estão chamando objetos em seus respectivos ambientes. Sempre que o cliente gerenciado chama um método em um objeto COM, o tempo de execução cria um [RCW](../../../docs/framework/interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper). Os RCWs eliminam as diferenças entre os mecanismos de referência gerenciada e não gerenciada, entre outras coisas. O tempo de execução também cria um [CCW](../../../docs/framework/interop/com-callable-wrapper.md) (COM Callable Wrapper) para reverter o processo, permitindo que um cliente COM chame um método em um objeto .NET diretamente. Como mostra a ilustração a seguir, a perspectiva do código de chamada determina qual classe wrapper é criada pelo tempo de execução.  
  
 ![Visão geral do wrapper COM](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")  
Visão geral do wrapper COM  
  
 Na maioria dos casos, o RCW padrão ou o CCW gerado pelo tempo de execução fornece o marshaling adequado para chamadas que cruzam o limite entre o COM e o .NET Framework. Usando atributos personalizados, opcionalmente, você pode ajustar a maneira como o tempo de execução representa o código gerenciado e não gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Interoperabilidade COM avançada](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [RCW (Runtime Callable Wrapper)](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md)  
 [Personalizando Wrappers padrão](http://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d)  
 [Como personalizar RCWs (Runtime Callable Wrappers)](http://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732)
