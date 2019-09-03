---
title: Como expor componentes .NET ao COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 981f5f23bf2aafc41426c858e150ec3664a494f9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205810"
---
# <a name="exposing-net-components-to-com"></a>Como expor componentes .NET ao COM

A escrita de um tipo .NET e o consumo desse tipo em um código não gerenciado são atividades distintas para desenvolvedores. Esta seção descreve várias dicas para escrever um código gerenciado que interopera com clientes COM:

- [Qualificando tipos .NET para interoperação](../../standard/native-interop/qualify-net-types-for-interoperation.md).

     Todos os tipos gerenciados, métodos, propriedades, campos e eventos que você deseja expor ao COM devem ser públicos. Os tipos devem ter um construtor sem parâmetros público, que é o único construtor que pode ser invocado por meio do COM.

- [Aplicando atributos de interoperabilidade](../../standard/native-interop/apply-interop-attributes.md).

     Atributos personalizados no código gerenciado podem melhorar a interoperabilidade de um componente.

- [Empacotando um assembly para o COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).

     Os desenvolvedores do COM podem precisar que você resuma as etapas envolvidas na referência e implantação dos assemblies.

 Além disso, esta seção identifica as tarefas relacionadas ao consumo de um tipo gerenciado em um cliente COM.

## <a name="to-consume-a-managed-type-from-com"></a>Para consumir um tipo gerenciado por meio do COM

1. [Registrar assemblies com o COM](../../../docs/framework/interop/registering-assemblies-with-com.md).

     Os tipos em um assembly (e as bibliotecas de tipos) devem ser registrados em tempo de design. Se um instalador não registrar o assembly, instrua os desenvolvedores do COM a usar Regasm.exe.

2. [Referenciar tipos .NET por meio do COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).

     Os desenvolvedores do COM podem referenciar tipos em um assembly usando as mesmas ferramentas e técnicas que usam hoje.

3. [Chamar um objeto .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).

     Os desenvolvedores do COM podem chamar métodos no objeto .NET da mesma forma que chamam métodos em qualquer tipo não gerenciado. Por exemplo, a API **CoCreateInstance** do COM ativa objetos .NET.

4. [Implante um aplicativo para o acesso COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).

     Um assembly de nome forte pode ser instalado no cache de assembly global e exige uma assinatura de seu fornecedor. Os assemblies que não têm nome forte devem ser instalados no diretório do aplicativo do cliente.

## <a name="see-also"></a>Consulte também

- [Interoperação com código não gerenciado](../../../docs/framework/interop/index.md)
- [Amostra de interoperabilidade COM: Cliente COM e servidor .NET](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
