---
title: 'Como: Personalizar classes de entidade usando o editor de códigos'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: f57b07d03297347561b6b2e2634038aa1f29bc40
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="bbaa2-102">Como: Personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="bbaa2-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="bbaa2-103">Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar ou personalizar suas classes de entidade.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-103">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="bbaa2-104">Você também pode usar o editor de códigos do Visual Studio para escrever seu próprio código de mapeamento ou para personalizar o código que já foi gerado.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-104">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="bbaa2-105">Para obter mais informações, consulte [mapeamento baseado no atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="bbaa2-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="bbaa2-106">Os tópicos desta seção descrevem como personalizar o modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="bbaa2-107">Como especificar nomes de banco de dados</span><span class="sxs-lookup"><span data-stu-id="bbaa2-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="bbaa2-108">Descreve como usar o <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="bbaa2-109">Como representar Tabelas como Classes</span><span class="sxs-lookup"><span data-stu-id="bbaa2-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="bbaa2-110">Descreve como usar o <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="bbaa2-111">Como representar colunas como membros de classe</span><span class="sxs-lookup"><span data-stu-id="bbaa2-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="bbaa2-112">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="bbaa2-113">Como representar chaves primárias</span><span class="sxs-lookup"><span data-stu-id="bbaa2-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="bbaa2-114">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="bbaa2-115">Como mapear relações de banco de dados</span><span class="sxs-lookup"><span data-stu-id="bbaa2-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="bbaa2-116">Fornece exemplos de como usar o atributo <xref:System.Data.Linq.Mapping.AssociationAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="bbaa2-117">Como representar colunas como geradas por banco de dados</span><span class="sxs-lookup"><span data-stu-id="bbaa2-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="bbaa2-118">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="bbaa2-119">Como representar colunas como colunas de Carimbo de data/hora ou de Versão</span><span class="sxs-lookup"><span data-stu-id="bbaa2-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="bbaa2-120">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="bbaa2-121">Como especificar tipos de dados do banco de dados</span><span class="sxs-lookup"><span data-stu-id="bbaa2-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="bbaa2-122">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="bbaa2-123">Como representar colunas calculadas</span><span class="sxs-lookup"><span data-stu-id="bbaa2-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="bbaa2-124">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="bbaa2-125">Como especificar campos de armazenamento particular</span><span class="sxs-lookup"><span data-stu-id="bbaa2-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="bbaa2-126">Descreve como usar o <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="bbaa2-127">Como representar colunas que permitem valores nulos</span><span class="sxs-lookup"><span data-stu-id="bbaa2-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="bbaa2-128">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="bbaa2-129">Como mapear hierarquias de herança</span><span class="sxs-lookup"><span data-stu-id="bbaa2-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="bbaa2-130">Descreve os mapeamentos necessários para especificar uma hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="bbaa2-131">Como especificar a verificação de conflitos de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="bbaa2-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="bbaa2-132">Descreve como usar o <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbaa2-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbaa2-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbaa2-133">See Also</span></span>  
 [<span data-ttu-id="bbaa2-134">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="bbaa2-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
