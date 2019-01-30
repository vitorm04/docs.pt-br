---
title: Expondo componentes do .NET Framework para COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5c80ba473b0080a1368c82949c765820239ef25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715732"
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
  
3.  [Chamar um objeto .NET](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100)).  
  
     Os desenvolvedores do COM podem chamar métodos no objeto .NET da mesma forma que chamam métodos em qualquer tipo não gerenciado. Por exemplo, a API **CoCreateInstance** do COM ativa objetos .NET.  
  
4.  [Implante um aplicativo para o acesso COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100)).  
  
     Um assembly de nome forte pode ser instalado no cache de assembly global e exige uma assinatura de seu fornecedor. Os assemblies que não têm nome forte devem ser instalados no diretório do aplicativo do cliente.  
  
## <a name="see-also"></a>Consulte também
- [Interoperação com código não gerenciado](../../../docs/framework/interop/index.md)
- [Amostra de interoperabilidade COM: Cliente COM e servidor .NET](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
