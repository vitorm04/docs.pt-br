---
title: Inferir colunas
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 651d132fd76ba9015d4730a5e519bc679608e275
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203596"
---
# <a name="inferring-columns"></a><span data-ttu-id="0a0b5-102">Inferir colunas</span><span class="sxs-lookup"><span data-stu-id="0a0b5-102">Inferring Columns</span></span>
<span data-ttu-id="0a0b5-103">Depois que ADO.net foi determinado de um documento XML que elementos são inferidos como <xref:System.Data.DataSet>tabelas para um, ele infere as colunas para essas tabelas.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="0a0b5-104">O ADO.NET 2,0 introduziu um novo mecanismo de inferência de esquema que infere um tipo de dados fortemente tipado para cada elemento simpleType.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="0a0b5-105">Em versões anteriores, o tipo de dados de um elemento **SimpleProperty** inferido era sempre **xsd: String**.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="0a0b5-106">Migração e compatibilidade com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="0a0b5-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="0a0b5-107">O método **ReadXml** usa um argumento do tipo **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="0a0b5-108">Esse argumento permite que você especifique o comportamento de inferência compatível com as versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="0a0b5-109">Os valores disponíveis para a enumeração **InferSchema** são mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="0a0b5-110">Fornece compatibilidade com versões anteriores, sempre informando um <xref:System.String>tipo simples como.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="0a0b5-111">Infere um tipo de dados fortemente tipado.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="0a0b5-112">Gera uma exceção se usada com um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="0a0b5-113">Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="0a0b5-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a0b5-114">Attributes</span></span>  
 <span data-ttu-id="0a0b5-115">Conforme definido em [tabelas de referência](inferring-tables.md), um elemento com atributos será inferido como uma tabela.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-115">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="0a0b5-116">Os atributos desse elemento serão inferidos como colunas para a tabela.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="0a0b5-117">A propriedade **ColumnMapping** das colunas será definida como MappingType **. Attribute**, para garantir que os nomes de coluna serão gravados como atributos se o esquema for gravado novamente em XML.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="0a0b5-118">Os valores dos atributos são armazenados em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="0a0b5-119">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="0a0b5-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0a0b5-120">O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas, **attr1** e **attr2**.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="0a0b5-121">A propriedade **ColumnMapping** de ambas as colunas será definida como **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="0a0b5-122">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0a0b5-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0a0b5-123">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="0a0b5-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0a0b5-124">attr1</span><span class="sxs-lookup"><span data-stu-id="0a0b5-124">attr1</span></span>|<span data-ttu-id="0a0b5-125">attr2</span><span class="sxs-lookup"><span data-stu-id="0a0b5-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="0a0b5-126">value1</span><span class="sxs-lookup"><span data-stu-id="0a0b5-126">value1</span></span>|<span data-ttu-id="0a0b5-127">value2</span><span class="sxs-lookup"><span data-stu-id="0a0b5-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="0a0b5-128">Elementos sem atributos ou elementos filho</span><span class="sxs-lookup"><span data-stu-id="0a0b5-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="0a0b5-129">Se um elemento não tiver elementos filho ou atributos, ele será inferido como uma coluna.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="0a0b5-130">A propriedade **ColumnMapping** da coluna será definida como MappingType **. Element**.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="0a0b5-131">O texto para elementos filho é armazenado em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="0a0b5-132">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="0a0b5-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0a0b5-133">O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas, **ChildElement1** e **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="0a0b5-134">A propriedade **ColumnMapping** de ambas as colunas será definida como **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="0a0b5-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="0a0b5-135">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0a0b5-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0a0b5-136">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="0a0b5-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0a0b5-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0a0b5-137">ChildElement1</span></span>|<span data-ttu-id="0a0b5-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="0a0b5-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="0a0b5-139">Texto1</span><span class="sxs-lookup"><span data-stu-id="0a0b5-139">Text1</span></span>|<span data-ttu-id="0a0b5-140">Empresa2</span><span class="sxs-lookup"><span data-stu-id="0a0b5-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a0b5-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a0b5-141">See also</span></span>

- [<span data-ttu-id="0a0b5-142">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="0a0b5-142">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="0a0b5-143">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="0a0b5-143">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="0a0b5-144">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="0a0b5-144">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="0a0b5-145">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="0a0b5-145">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="0a0b5-146">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="0a0b5-146">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="0a0b5-147">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0a0b5-147">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
