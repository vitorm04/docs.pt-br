---
title: Inferir colunas
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 53e77f624c5af8f61a32d5b1399d2728f32011a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034275"
---
# <a name="inferring-columns"></a><span data-ttu-id="c9aab-102">Inferir colunas</span><span class="sxs-lookup"><span data-stu-id="c9aab-102">Inferring Columns</span></span>
<span data-ttu-id="c9aab-103">Depois que o ADO.NET determinou de um documento XML que elementos inferir como tabelas para um <xref:System.Data.DataSet>, ele infere, em seguida, as colunas para essas tabelas.</span><span class="sxs-lookup"><span data-stu-id="c9aab-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="c9aab-104">O ADO.NET 2.0 introduziu um novo mecanismo de inferência de esquema que infere um tipo de dados fortemente tipado para cada **simpleType** elemento.</span><span class="sxs-lookup"><span data-stu-id="c9aab-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="c9aab-105">Nas versões anteriores, o tipo de dados de um inferido **simpleType** elemento era sempre **xsd: string**.</span><span class="sxs-lookup"><span data-stu-id="c9aab-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="c9aab-106">Migração e compatibilidade com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="c9aab-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="c9aab-107">O **ReadXml** método usa um argumento do tipo **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="c9aab-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="c9aab-108">Esse argumento permite que você especifique o comportamento de inferência de tipos compatível com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c9aab-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="c9aab-109">Os valores disponíveis para o **InferSchema** enumeração são mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c9aab-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="c9aab-110">Fornece compatibilidade com versões anteriores, sempre inferir um tipo simples como <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9aab-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="c9aab-111">Deduz um tipo de dados fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="c9aab-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="c9aab-112">Gera uma exceção se usado com um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="c9aab-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="c9aab-113">Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.</span><span class="sxs-lookup"><span data-stu-id="c9aab-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="c9aab-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9aab-114">Attributes</span></span>  
 <span data-ttu-id="c9aab-115">Conforme definido em [inferindo tabelas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), um elemento com atributos será inferido como uma tabela.</span><span class="sxs-lookup"><span data-stu-id="c9aab-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="c9aab-116">Os atributos desse elemento, em seguida, serão inferidos como colunas da tabela.</span><span class="sxs-lookup"><span data-stu-id="c9aab-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="c9aab-117">O **ColumnMapping** propriedade das colunas será definida como **MappingType.Attribute**, para garantir que os nomes de coluna serão gravados como atributos se o esquema é gravado de volta para XML.</span><span class="sxs-lookup"><span data-stu-id="c9aab-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="c9aab-118">Os valores dos atributos são armazenados em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="c9aab-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="c9aab-119">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="c9aab-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="c9aab-120">O processo de inferência produzirá uma tabela denominada **Element1** com duas colunas, **attr1** e **attr2**.</span><span class="sxs-lookup"><span data-stu-id="c9aab-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="c9aab-121">O **ColumnMapping** definirá a propriedade de ambas as colunas **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="c9aab-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="c9aab-122">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="c9aab-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="c9aab-123">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="c9aab-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="c9aab-124">attr1</span><span class="sxs-lookup"><span data-stu-id="c9aab-124">attr1</span></span>|<span data-ttu-id="c9aab-125">attr2</span><span class="sxs-lookup"><span data-stu-id="c9aab-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="c9aab-126">value1</span><span class="sxs-lookup"><span data-stu-id="c9aab-126">value1</span></span>|<span data-ttu-id="c9aab-127">value2</span><span class="sxs-lookup"><span data-stu-id="c9aab-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="c9aab-128">Elementos sem atributos ou elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9aab-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="c9aab-129">Se um elemento não tiver elementos filho ou atributos, ele será inferido como uma coluna.</span><span class="sxs-lookup"><span data-stu-id="c9aab-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="c9aab-130">O **ColumnMapping** propriedade da coluna será definida como **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="c9aab-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="c9aab-131">O texto para elementos filho é armazenado em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="c9aab-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="c9aab-132">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="c9aab-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="c9aab-133">O processo de inferência produzirá uma tabela denominada **Element1** com duas colunas, **ChildElement1** e **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="c9aab-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="c9aab-134">O **ColumnMapping** definirá a propriedade de ambas as colunas **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="c9aab-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="c9aab-135">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="c9aab-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="c9aab-136">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="c9aab-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="c9aab-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="c9aab-137">ChildElement1</span></span>|<span data-ttu-id="c9aab-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="c9aab-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="c9aab-139">Texto1</span><span class="sxs-lookup"><span data-stu-id="c9aab-139">Text1</span></span>|<span data-ttu-id="c9aab-140">Texto2</span><span class="sxs-lookup"><span data-stu-id="c9aab-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9aab-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9aab-141">See also</span></span>

- [<span data-ttu-id="c9aab-142">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="c9aab-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="c9aab-143">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="c9aab-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="c9aab-144">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="c9aab-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="c9aab-145">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="c9aab-145">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="c9aab-146">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="c9aab-146">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="c9aab-147">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c9aab-147">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
