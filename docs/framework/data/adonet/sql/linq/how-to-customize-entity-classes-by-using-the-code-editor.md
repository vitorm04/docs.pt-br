---
title: 'Como: personalizar classes de entidade usando o editor de códigos'
ms.date: 03/30/2017
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
ms.openlocfilehash: 578e0cbd1f6990a5d41007ad31f4c1c938cd3ebe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793798"
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="20d9f-102">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="20d9f-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="20d9f-103">Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para criar ou personalizar suas classes de entidade.</span><span class="sxs-lookup"><span data-stu-id="20d9f-103">Developers using Visual Studio can use the Object Relational Designer to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="20d9f-104">Você também pode usar o editor de código do Visual Studio para escrever seu próprio código de mapeamento ou para personalizar o código que já foi gerado.</span><span class="sxs-lookup"><span data-stu-id="20d9f-104">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="20d9f-105">Para obter mais informações, consulte [mapeamento baseado em atributo](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="20d9f-105">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="20d9f-106">Os tópicos desta seção descrevem como personalizar o modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="20d9f-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="20d9f-107">Como: Especificar nomes de banco de dados</span><span class="sxs-lookup"><span data-stu-id="20d9f-107">How to: Specify Database Names</span></span>](how-to-specify-database-names.md)  
 <span data-ttu-id="20d9f-108">Descreve como usar o <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="20d9f-109">Como: Representar tabelas como classes</span><span class="sxs-lookup"><span data-stu-id="20d9f-109">How to: Represent Tables as Classes</span></span>](how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="20d9f-110">Descreve como usar o <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="20d9f-111">Como: Representar colunas como membros de classe</span><span class="sxs-lookup"><span data-stu-id="20d9f-111">How to: Represent Columns as Class Members</span></span>](how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="20d9f-112">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="20d9f-113">Como: Representar chaves primárias</span><span class="sxs-lookup"><span data-stu-id="20d9f-113">How to: Represent Primary Keys</span></span>](how-to-represent-primary-keys.md)  
 <span data-ttu-id="20d9f-114">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="20d9f-115">Como: Mapear relações de banco de dados</span><span class="sxs-lookup"><span data-stu-id="20d9f-115">How to: Map Database Relationships</span></span>](how-to-map-database-relationships.md)  
 <span data-ttu-id="20d9f-116">Fornece exemplos de como usar o atributo <xref:System.Data.Linq.Mapping.AssociationAttribute>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="20d9f-117">Como: Representar colunas como geradas pelo banco de dados</span><span class="sxs-lookup"><span data-stu-id="20d9f-117">How to: Represent Columns as Database-Generated</span></span>](how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="20d9f-118">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="20d9f-119">Como: Representar colunas como carimbo de data/hora ou colunas de versão</span><span class="sxs-lookup"><span data-stu-id="20d9f-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="20d9f-120">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="20d9f-121">Como: Especificar tipos de dados de banco</span><span class="sxs-lookup"><span data-stu-id="20d9f-121">How to: Specify Database Data Types</span></span>](how-to-specify-database-data-types.md)  
 <span data-ttu-id="20d9f-122">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="20d9f-123">Como: Representar colunas computadas</span><span class="sxs-lookup"><span data-stu-id="20d9f-123">How to: Represent Computed Columns</span></span>](how-to-represent-computed-columns.md)  
 <span data-ttu-id="20d9f-124">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="20d9f-125">Como: Especificar campos de armazenamento privado</span><span class="sxs-lookup"><span data-stu-id="20d9f-125">How to: Specify Private Storage Fields</span></span>](how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="20d9f-126">Descreve como usar o <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="20d9f-127">Como: Representar colunas como permitindo valores nulos</span><span class="sxs-lookup"><span data-stu-id="20d9f-127">How to: Represent Columns as Allowing Null Values</span></span>](how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="20d9f-128">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="20d9f-129">Como: Mapear hierarquias de herança</span><span class="sxs-lookup"><span data-stu-id="20d9f-129">How to: Map Inheritance Hierarchies</span></span>](how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="20d9f-130">Descreve os mapeamentos necessários para especificar uma hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="20d9f-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="20d9f-131">Como: Especificar verificação de conflito de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="20d9f-131">How to: Specify Concurrency-Conflict Checking</span></span>](how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="20d9f-132">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="20d9f-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d9f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20d9f-133">See also</span></span>

- [<span data-ttu-id="20d9f-134">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="20d9f-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
