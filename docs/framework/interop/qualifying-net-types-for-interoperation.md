---
title: "Qualificando tipos do .NET para interoperação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 68ecd5e4c562f1eecb31ee539adb70d67455a584
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="qualifying-net-types-for-interoperation"></a>Qualificando tipos do .NET para interoperação
Se você pretende expor os tipos em um assembly para aplicativos COM, considere os requisitos de interoperabilidade COM em tempo de design. Tipos gerenciados (classe, interface, estrutura e enumeração) se integram perfeitamente com tipos COM quando você obedece às seguintes diretrizes:  
  
-   As classes devem implementar interfaces explicitamente.  
  
     Embora a interoperabilidade COM forneça um mecanismo para gerar automaticamente uma interface contendo todos os membros da classe e os membros da respectiva classe base, é muito melhor fornecer interfaces explícitas. A interface gerada automaticamente é chamada de interface de classe. Para obter diretrizes, consulte [Introdução à interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).  
  
     Você pode usar [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# e C++ para incorporar as definições de interface no seu código, em vez de usar a linguagem IDL ou um equivalente dela. Para obter detalhes da sintaxe, consulte a documentação da linguagem.  
  
-   Os tipos gerenciados devem ser públicos.  
  
     Somente os tipos públicos em um assembly são registrados e exportados para a biblioteca de tipos. Como resultado, somente os tipos públicos são visíveis para COM.  
  
     Tipos gerenciados expõem recursos para outro código gerenciado que pode não ser exposto a COM. Por exemplo, campos de constantes, construtores com parâmetros e métodos estáticos não são expostos a clientes COM. Além disso, como o tempo de execução realiza marshaling de dados dentro e fora de um tipo, os dados podem ser copiados ou transformados.  
  
-   Propriedades, métodos, campos e eventos devem ser públicos.  
  
     Membros de tipos públicos também devem ser públicos para ser visíveis para COM. Você pode restringir a visibilidade de um assembly, um tipo público ou membros públicos de um tipo público aplicando o <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Por padrão, todos os membros e tipos públicos são visíveis.  
  
-   Os tipos devem ter um construtor padrão público para serem ativados do COM.  
  
     Tipos públicos gerenciados são visíveis para o COM. No entanto, sem um construtor público padrão (um construtor sem argumentos), clientes COM não podem criar o tipo. Clientes COM ainda podem usar o tipo se ele é ativado por outros meios.  
  
-   Os tipos não podem ser abstratos.  
  
     Nem clientes COM, tampouco clientes .NET podem criar tipos abstratos.  
  
 Quando exportados para COM, a hierarquia de herança de um tipo gerenciado é nivelada. O controle de versão também difere entre ambientes gerenciados e não gerenciados. Os tipos expostos ao COM não têm as mesmas características de controle de versão de outros tipos gerenciados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 [Expondo componentes do .NET Framework para COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [Introdução à Interface de Classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Aplicando atributos de interoperabilidade](../../../docs/framework/interop/applying-interop-attributes.md)   
 [Empacotando um assembly para COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)

