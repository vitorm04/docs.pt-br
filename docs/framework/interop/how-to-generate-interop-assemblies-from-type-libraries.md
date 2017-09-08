---
title: Como gerar assemblies de interoperabilidade a partir de bibliotecas de tipos
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
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ff406fb14a21b0425444d04e98bbaca127d3687b
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Como gerar assemblies de interoperabilidade a partir de bibliotecas de tipos
O [Importador da Biblioteca de Tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) é uma ferramenta de linha de comando que converte as classes e interfaces contidas em uma biblioteca de tipos COM em metadados. Essa ferramenta cria automaticamente um assembly de interoperabilidade e o namespace para as informações de tipo. Depois que os metadados de uma classe estiverem disponíveis, os clientes gerenciados podem criar instâncias do tipo COM e chamar os métodos dele, como se fosse uma instância do .NET. O Tlbimp.exe converte uma biblioteca de tipos inteira em metadados de uma só vez e não é capaz de gerar informações de tipo para um subconjunto dos tipos definidos em uma biblioteca de tipos.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Para gerar um assembly de interoperabilidade de uma biblioteca de tipos  
  
1.  Use o seguinte comando:  
  
     **tlbimp** \<*type-library-file*>  
  
     Adicionar a opção **/out:** produz um assembly de interoperabilidade com um nome alterado, como LOANLib.dll. A alteração do nome do assembly de interoperabilidade pode ajudar a diferenciá-lo da DLL COM original e evitar problemas que podem ocorrer devido a nomes duplicados.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir produz o assembly Loanlib.dll no namespace `Loanlib`.  
  
```  
tlbimp Loanlib.dll  
```  
  
 O comando a seguir produz um assembly de interoperabilidade com um nome alterado (LOANLib.dll).  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Consulte também  
 [Importando uma biblioteca de tipos como um assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [Expondo componentes do COM ao .NET Framework](../../../docs/framework/interop/exposing-com-components.md)

