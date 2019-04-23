---
title: 'Como: Obter as informações de tipo e membro de um assembly'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9d01715a9635b276ca87d94082bb4d3820084e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138873"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Como: Obter as informações de tipo e membro de um assembly
O namespace <xref:System.Reflection> contém vários métodos para obter informações de um assembly. Esta seção demonstra um desses métodos. Para saber mais, veja [Visão geral da reflexão](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 O exemplo a seguir obtém informações de tipo e membro de um assembly.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>Consulte também

- [Programação com domínios do aplicativo](./application-domains.md#programming-with-application-domains)
- [Reflexão](../../../docs/framework/reflection-and-codedom/reflection.md)
- [Usar domínios do aplicativo](../../../docs/framework/app-domains/use.md)
