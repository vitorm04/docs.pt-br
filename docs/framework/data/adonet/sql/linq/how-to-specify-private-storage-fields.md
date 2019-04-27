---
title: 'Como: especificar campos de armazenamento particular'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: 843b7ae8dbddb76e0e5fa33d3594a5655dbf1a37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902714"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="a2327-102">Como: especificar campos de armazenamento particular</span><span class="sxs-lookup"><span data-stu-id="a2327-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="a2327-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> propriedade no <xref:System.Data.Linq.Mapping.DataAttribute> atributo para designar o nome de um campo de armazenamento subjacente.</span><span class="sxs-lookup"><span data-stu-id="a2327-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="a2327-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2327-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="a2327-105">Para especificar o nome de um armazenamento subjacente coloque</span><span class="sxs-lookup"><span data-stu-id="a2327-105">To specify the name of an underlying storage field</span></span>  
  
1. <span data-ttu-id="a2327-106">Adicione a propriedade de <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="a2327-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="a2327-107">Atribua o nome do campo como o valor da propriedade de <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> .</span><span class="sxs-lookup"><span data-stu-id="a2327-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2327-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2327-108">See also</span></span>

- [<span data-ttu-id="a2327-109">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a2327-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a2327-110">Como: Personalizar Classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="a2327-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
