---
title: 'Como: especificar nomes de banco de dados'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 1c694678dc3a60cf91dea62f2a17973b396e2b19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184516"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="92642-102">Como: especificar nomes de banco de dados</span><span class="sxs-lookup"><span data-stu-id="92642-102">How to: Specify Database Names</span></span>
<span data-ttu-id="92642-103">Use a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> em um atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para especificar o nome de uma base de dados quando um nome não é fornecido pela conexão.</span><span class="sxs-lookup"><span data-stu-id="92642-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="92642-104">Para exemplos de códigos, consulte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="92642-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="92642-105">Para especificar o nome de base de dados</span><span class="sxs-lookup"><span data-stu-id="92642-105">To specify the name of the database</span></span>  
  
1.  <span data-ttu-id="92642-106">Adicione o atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para a declaração de classe para o base de dados.</span><span class="sxs-lookup"><span data-stu-id="92642-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2.  <span data-ttu-id="92642-107">Adicione a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> ao atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> .</span><span class="sxs-lookup"><span data-stu-id="92642-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="92642-108">Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> o nome que você deseja especificar.</span><span class="sxs-lookup"><span data-stu-id="92642-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92642-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92642-109">See also</span></span>

- [<span data-ttu-id="92642-110">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="92642-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="92642-111">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="92642-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
