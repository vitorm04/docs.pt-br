---
title: "Como criar um domínio de aplicativo | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 928a5d897e7df288f07ec32aff43f28617ef9623
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="how-to-create-an-application-domain"></a>Como criar um domínio de aplicativo
Um host Common Language Runtime cria domínios de aplicativos automaticamente quando eles são necessários. No entanto, você pode criar seus próprios domínios dos aplicativos e carregá-los nos assemblies que você deseja gerenciar pessoalmente. Você também pode criar domínios do aplicativo do qual o código é executado.  
  
 Crie um novo domínio do aplicativo usando um dos métodos **CreateDomain** sobrecarregados na classe <xref:System.AppDomain?displayProperty=fullName>. Você pode dar ao domínio do aplicativo um nome e referenciá-lo por esse nome.  
  
 O exemplo a seguir cria um novo domínio do aplicativo, atribui a ele o nome `MyDomain` e, em seguida, imprime o nome do domínio do host e o domínio do aplicativo filho recém-criado no console.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)] [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)] [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Programação com domínios do aplicativo](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Uso de domínios do aplicativo](../../../docs/framework/app-domains/use.md)
