---
title: Como obter as informações de tipo e membro de um assembly
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
ms.openlocfilehash: 44fcded298f33a420a505900f618c1c67f4b9b6f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50180056"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Como obter as informações de tipo e membro de um assembly
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
