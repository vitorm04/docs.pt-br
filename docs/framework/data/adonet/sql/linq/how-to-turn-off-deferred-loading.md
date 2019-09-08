---
title: 'Como: desligar o carregamento adiado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781660"
---
# <a name="how-to-turn-off-deferred-loading"></a>Como: desligar o carregamento adiado
Você pode desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`. Para obter mais informações, veja [carregamento deferido versus imediato](deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> A carga adiada é desativada implicitamente quando o rastreamento de objeto é desativado. Para obter mais informações, confira [Como: Recuperar informações como somente](how-to-retrieve-information-as-read-only.md)leitura.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Conceitos de consulta](query-concepts.md)
- [Consultando o banco de dados](querying-the-database.md)
