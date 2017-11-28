---
title: Expondo componentes do .NET Framework para COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9451504b64ddaa8dc0ea6b3a0754257b2c8b3824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-net-framework-components-to-com"></a>Expondo componentes do .NET Framework para COM
A escrita de um tipo .NET e o consumo desse tipo em um código não gerenciado são atividades distintas para desenvolvedores. Esta seção descreve várias dicas para escrever um código gerenciado que interopera com clientes COM:  
  
-   [Qualificando tipos .NET para interoperação](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Todos os tipos gerenciados, métodos, propriedades, campos e eventos que você deseja expor ao COM devem ser públicos. Os tipos devem ter um construtor padrão público, que é o único construtor que pode ser invocado por meio do COM.  
  
-   [Aplicando atributos de interoperabilidade](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Atributos personalizados no código gerenciado podem melhorar a interoperabilidade de um componente.  
  
-   [Empacotando um assembly para o COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     Os desenvolvedores do COM podem precisar que você resuma as etapas envolvidas na referência e implantação dos assemblies.  
  
 Além disso, esta seção identifica as tarefas relacionadas ao consumo de um tipo gerenciado em um cliente COM.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>Para consumir um tipo gerenciado por meio do COM  
  
1.  [Registrar assemblies com o COM](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Os tipos em um assembly (e as bibliotecas de tipos) devem ser registrados em tempo de design. Se um instalador não registrar o assembly, instrua os desenvolvedores do COM a usar Regasm.exe.  
  
2.  [Referenciar tipos .NET por meio do COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     Os desenvolvedores do COM podem referenciar tipos em um assembly usando as mesmas ferramentas e técnicas que usam hoje.  
  
3.  [Chamar um objeto .NET](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).  
  
     Os desenvolvedores do COM podem chamar métodos no objeto .NET da mesma forma que chamam métodos em qualquer tipo não gerenciado. Por exemplo, a API **CoCreateInstance** do COM ativa objetos .NET.  
  
4.  [Implante um aplicativo para o acesso COM](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).  
  
     Um assembly de nome forte pode ser instalado no cache de assembly global e exige uma assinatura de seu fornecedor. Os assemblies que não têm nome forte devem ser instalados no diretório do aplicativo do cliente.  
  
## <a name="see-also"></a>Consulte também  
 [Interoperação com código não gerenciado](../../../docs/framework/interop/index.md)  
 [Amostra de interoperabilidade COM: cliente COM e servidor .NET](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
