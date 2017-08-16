---
title: "Como obter as informações de tipo e membro de um assembly | Microsoft Docs"
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
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 42a950493d6042581d98d3be3f4787df9752af16
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Como obter as informações de tipo e membro de um assembly
O namespace <xref:System.Reflection> contém vários métodos para obter informações de um assembly. Esta seção demonstra um desses métodos. Para saber mais, veja [Visão geral da reflexão](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 O exemplo a seguir obtém informações de tipo e membro de um assembly.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)] [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)] [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>Consulte também  
 [Programação com domínios do aplicativo](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Reflexão](../../../docs/framework/reflection-and-codedom/reflection.md)   
 [Usar domínios do aplicativo](../../../docs/framework/app-domains/use.md)
