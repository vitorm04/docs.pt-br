---
title: 'Como: especificar nomes de banco de dados'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 0daf754edf624410e0ea725acd6c266ccb7828dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781580"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="4d4a8-102">Como: especificar nomes de banco de dados</span><span class="sxs-lookup"><span data-stu-id="4d4a8-102">How to: Specify Database Names</span></span>
<span data-ttu-id="4d4a8-103">Use a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> em um atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para especificar o nome de uma base de dados quando um nome não é fornecido pela conexão.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="4d4a8-104">Para exemplos de códigos, consulte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="4d4a8-105">Para especificar o nome de base de dados</span><span class="sxs-lookup"><span data-stu-id="4d4a8-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="4d4a8-106">Adicione o atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para a declaração de classe para o base de dados.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="4d4a8-107">Adicione a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> ao atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4d4a8-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="4d4a8-108">Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> o nome que você deseja especificar.</span><span class="sxs-lookup"><span data-stu-id="4d4a8-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4a8-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d4a8-109">See also</span></span>

- [<span data-ttu-id="4d4a8-110">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4d4a8-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="4d4a8-111">Como: Personalizar classes de entidade usando o editor de código</span><span class="sxs-lookup"><span data-stu-id="4d4a8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
