---
title: Qualificando tipos do .NET para interoperação
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e57ec1a70aaae384f73b1ffdbf92e93fc0a7bdd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648556"
---
# <a name="qualifying-net-types-for-interoperation"></a>Qualificando tipos do .NET para interoperação
Se você pretende expor os tipos em um assembly para aplicativos COM, considere os requisitos de interoperabilidade COM em tempo de design. Tipos gerenciados (classe, interface, estrutura e enumeração) se integram perfeitamente com tipos COM quando você obedece às seguintes diretrizes:  
  
- As classes devem implementar interfaces explicitamente.  
  
     Embora a interoperabilidade COM forneça um mecanismo para gerar automaticamente uma interface contendo todos os membros da classe e os membros da respectiva classe base, é muito melhor fornecer interfaces explícitas. A interface gerada automaticamente é chamada de interface de classe. Para obter diretrizes, confira [Apresentando a interface de classe](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Você pode usar Visual Basic, C# e C++ para incorporar as definições de interface no código, em vez de usar a linguagem IDL ou uma equivalente. Para obter detalhes da sintaxe, consulte a documentação da linguagem.  
  
- Os tipos gerenciados devem ser públicos.  
  
     Somente os tipos públicos em um assembly são registrados e exportados para a biblioteca de tipos. Como resultado, somente os tipos públicos são visíveis para COM.  
  
     Tipos gerenciados expõem recursos para outro código gerenciado que pode não ser exposto a COM. Por exemplo, campos de constantes, construtores com parâmetros e métodos estáticos não são expostos a clientes COM. Além disso, como o tempo de execução realiza marshaling de dados dentro e fora de um tipo, os dados podem ser copiados ou transformados.  
  
- Propriedades, métodos, campos e eventos devem ser públicos.  
  
     Membros de tipos públicos também devem ser públicos para ser visíveis para COM. Você pode restringir a visibilidade de um assembly, um tipo público ou membros públicos de um tipo público aplicando o <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Por padrão, todos os membros e tipos públicos são visíveis.  
  
- Os tipos devem ter um construtor padrão público para serem ativados do COM.  
  
     Tipos públicos gerenciados são visíveis para o COM. No entanto, sem um construtor público padrão (um construtor sem argumentos), clientes COM não podem criar o tipo. Clientes COM ainda podem usar o tipo se ele é ativado por outros meios.  
  
- Os tipos não podem ser abstratos.  
  
     Nem clientes COM, tampouco clientes .NET podem criar tipos abstratos.  
  
 Quando exportados para COM, a hierarquia de herança de um tipo gerenciado é nivelada. O controle de versão também difere entre ambientes gerenciados e não gerenciados. Os tipos expostos ao COM não têm as mesmas características de controle de versão de outros tipos gerenciados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [Expondo componentes do .NET Framework ao COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Apresentando a interface de classe](com-callable-wrapper.md#introducing-the-class-interface)
- [Aplicando atributos de interoperabilidade](../../../docs/framework/interop/applying-interop-attributes.md)
- [Empacotando um assembly para COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
