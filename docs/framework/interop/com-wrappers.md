---
title: Wrappers COM
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d02d1b170362a5175fb24d68b00e4648819541e
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092651"
---
# <a name="com-wrappers"></a>Wrappers COM
O COM difere do modelo de objeto .NET Framework de várias maneiras importantes:  
  
-   Os clientes de objetos COM devem gerenciar o tempo de vida desses objetos; o Common Language Runtime gerencia o tempo de vida de objetos em seu ambiente.  
  
-   Os clientes de objetos COM descobrem se um serviço está disponível solicitando uma interface que fornece esse serviço e recebendo um ponteiro de interface ou não. Os clientes de objetos .NET podem obter uma descrição da funcionalidade de um objeto usando a reflexão.  
  
-   Os objetos .NET residem na memória gerenciada pelo ambiente de execução do .NET Framework. O ambiente de execução pode mover objetos na memória por motivos de desempenho e atualizar todas as referências nos objetos movidos por ele. Os clientes não gerenciados, depois de obter um ponteiro para um objeto, dependem do objeto para permanecerem no mesmo local. Esses clientes não têm nenhum mecanismo para lidar com um objeto cujo local não é fixo.  
  
 Para superar essas diferenças, o tempo de execução fornece classes wrapper para fazer com que os clientes gerenciados e não gerenciados acreditem que estão chamando objetos em seus respectivos ambientes. Sempre que o cliente gerenciado chama um método em um objeto COM, o tempo de execução cria um [RCW](runtime-callable-wrapper.md) (Runtime Callable Wrapper). Os RCWs eliminam as diferenças entre os mecanismos de referência gerenciada e não gerenciada, entre outras coisas. O tempo de execução também cria um [CCW](com-callable-wrapper.md) (COM Callable Wrapper) para reverter o processo, permitindo que um cliente COM chame um método em um objeto .NET diretamente. Como mostra a ilustração a seguir, a perspectiva do código de chamada determina qual classe wrapper é criada pelo tempo de execução.  
  
 ![Visão geral do wrapper COM](media/bidirectional.gif "bidirectional")  
Visão geral do wrapper COM  
  
 Na maioria dos casos, o RCW padrão ou o CCW gerado pelo tempo de execução fornece o marshaling adequado para chamadas que cruzam o limite entre o COM e o .NET Framework. Usando atributos personalizados, opcionalmente, você pode ajustar a maneira como o tempo de execução representa o código gerenciado e não gerenciado.  
  
## <a name="see-also"></a>Consulte também
- [Interoperabilidade COM avançada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [RCW (Runtime Callable Wrapper)](runtime-callable-wrapper.md)
- [COM Callable Wrapper](com-callable-wrapper.md)
- [Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)) (Personalizando wrappers padrão)
- [Como: Personalizar RCWs (Runtime Callable Wrappers)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))
