---
title: "Como: Personalizar classes de entidade usando o editor de códigos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d5586e28e784c43488245db814abf32d863232fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="8d776-102">Como: Personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="8d776-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="8d776-103">Os desenvolvedores que usam o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar ou personalizar suas classes de entidade.</span><span class="sxs-lookup"><span data-stu-id="8d776-103">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="8d776-104">Você também pode usar o editor de códigos do [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] para escrever seu próprio código de mapeamento ou para personalizar o código que já foi gerado.</span><span class="sxs-lookup"><span data-stu-id="8d776-104">You can also use the [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="8d776-105">Para obter mais informações, consulte [mapeamento baseado no atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="8d776-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="8d776-106">Os tópicos desta seção descrevem como personalizar o modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="8d776-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="8d776-107">Como: especificar nomes de banco de dados</span><span class="sxs-lookup"><span data-stu-id="8d776-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="8d776-108">Descreve como usar o <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="8d776-109">Como: representa tabelas como Classes</span><span class="sxs-lookup"><span data-stu-id="8d776-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="8d776-110">Descreve como usar o <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8d776-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="8d776-111">Como: representa colunas como membros de classe</span><span class="sxs-lookup"><span data-stu-id="8d776-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="8d776-112">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8d776-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="8d776-113">Como: representa chaves primárias</span><span class="sxs-lookup"><span data-stu-id="8d776-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="8d776-114">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="8d776-115">Como: mapear relações de banco de dados</span><span class="sxs-lookup"><span data-stu-id="8d776-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="8d776-116">Fornece exemplos de como usar o atributo <xref:System.Data.Linq.Mapping.AssociationAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8d776-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="8d776-117">Como: representa colunas como gerado pelo banco de dados</span><span class="sxs-lookup"><span data-stu-id="8d776-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="8d776-118">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="8d776-119">Como: representa colunas como colunas de versão ou carimbo de hora</span><span class="sxs-lookup"><span data-stu-id="8d776-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="8d776-120">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="8d776-121">Como: especificar tipos de dados do banco de dados</span><span class="sxs-lookup"><span data-stu-id="8d776-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="8d776-122">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="8d776-123">Como: representa colunas computadas</span><span class="sxs-lookup"><span data-stu-id="8d776-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="8d776-124">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="8d776-125">Como: especificar campos de armazenamento particular</span><span class="sxs-lookup"><span data-stu-id="8d776-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="8d776-126">Descreve como usar o <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="8d776-127">Como: representa colunas como permitir valores nulos</span><span class="sxs-lookup"><span data-stu-id="8d776-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="8d776-128">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="8d776-129">Como: mapear hierarquias de herança</span><span class="sxs-lookup"><span data-stu-id="8d776-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="8d776-130">Descreve os mapeamentos necessários para especificar uma hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="8d776-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="8d776-131">Como: especificar verificação de conflitos de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="8d776-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="8d776-132">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d776-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d776-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d776-133">See Also</span></span>  
 [<span data-ttu-id="8d776-134">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="8d776-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
