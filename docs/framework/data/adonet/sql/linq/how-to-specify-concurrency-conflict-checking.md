---
title: 'Como: especificar a verificação de conflito de simultaneidade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 7adacdccd12c6493ff7c62c0e6a44058a9719d7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197203"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="c01ee-102">Como: especificar a verificação de conflito de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="c01ee-102">How to: Specify Concurrency-Conflict Checking</span></span>

<span data-ttu-id="c01ee-103">Você pode especificar quais colunas de base de dados devem ser marcadas para ver se houver conflitos de simultaneidade quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="c01ee-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="c01ee-104">Para obter mais informações, consulte [como especificar quais membros são testados para conflitos de simultaneidade](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="c01ee-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c01ee-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c01ee-105">Example</span></span>  

 <span data-ttu-id="c01ee-106">O código a seguir especifica que o membro de `HomePage` nunca deve ser testado durante verificações de atualização.</span><span class="sxs-lookup"><span data-stu-id="c01ee-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="c01ee-107">Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="c01ee-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c01ee-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="c01ee-108">See also</span></span>

- [<span data-ttu-id="c01ee-109">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c01ee-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="c01ee-110">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="c01ee-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
