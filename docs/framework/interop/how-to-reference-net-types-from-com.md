---
title: 'Como: Referenciar tipos .NET por meio do COM'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5151d89feccbe68daa5a8de4aa3b75a42511899
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220264"
---
# <a name="how-to-reference-net-types-from-com"></a>Como: Referenciar tipos .NET por meio do COM
Do ponto de vista do código de cliente e servidor, as diferenças entre o .NET Framework e o COM são bastante invisíveis. Os clientes do Microsoft Visual Basic podem exibir um objeto .NET no Pesquisador de Objetos, que expõe os métodos de objeto e a sintaxe, propriedades e campos exatamente como se fosse qualquer outro objeto COM.  
  
 O processo de importação de uma biblioteca de tipos é um pouco mais complicado para clientes do C++, embora você use as mesmas ferramentas para exportar metadados para uma biblioteca de tipos COM. Para referenciar membros do objeto .NET de um cliente C++ não gerenciado, referencie o arquivo TLB (produzido com Tlbexp.exe) com a diretiva **#import**. Ao referenciar uma biblioteca de tipos C++, você deve especificar a opção **raw_interfaces_only** ou importar as definições na biblioteca de classes base, Mscorlib.tlb.  
  
### <a name="to-import-a-library"></a>Para importar uma biblioteca  
  
-   Especifique a opção **raw_interfaces_only** na diretiva **#import**. Por exemplo:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     - ou -  
  
-   Inclua uma diretiva #import para Mscorlib.tlb. Por exemplo:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Expondo componentes do .NET Framework ao COM](exposing-dotnet-components-to-com.md)
- [Registrando assemblies usando COM](registering-assemblies-with-com.md)
- [Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)) (Chamando um objeto .NET)
- [Implantando um aplicativo para acesso COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
