---
title: XmlSchemaSet para compilação de esquema
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c24fe637514ba773cecc7824de276b1707a4e90c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45676279"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="3f175-102">XmlSchemaSet para compilação de esquema</span><span class="sxs-lookup"><span data-stu-id="3f175-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="3f175-103">Descreve <xref:System.Xml.Schema.XmlSchemaSet>, um cache onde os esquemas de linguagem de definição de esquema XML (XSD) podem ser armazenados e validado.</span><span class="sxs-lookup"><span data-stu-id="3f175-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="3f175-104">A classe de XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3f175-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="3f175-105"><xref:System.Xml.Schema.XmlSchemaSet> é um cache onde os esquemas de linguagem de definição de esquema XML (XSD) podem ser armazenados e validado.</span><span class="sxs-lookup"><span data-stu-id="3f175-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="3f175-106">Na versão 1,0 de <xref:System.Xml?displayProperty=nameWithType> , os esquemas XML foram carregados em uma classe de <xref:System.Xml.Schema.XmlSchemaCollection> como uma biblioteca de esquemas.</span><span class="sxs-lookup"><span data-stu-id="3f175-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="3f175-107">Na versão 2,0 de <xref:System.Xml?displayProperty=nameWithType> , <xref:System.Xml.XmlValidatingReader> e as classes de <xref:System.Xml.Schema.XmlSchemaCollection> são obsoletos, e foram substituídas por métodos de <xref:System.Xml.XmlReader.Create%2A> , e a classe de <xref:System.Xml.Schema.XmlSchemaSet> respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3f175-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="3f175-108"><xref:System.Xml.Schema.XmlSchemaSet> foi introduzido para corrigir um número de problemas que incluem a compatibilidade de padrão, o desempenho, e o formato reduzido do esquema do Microsoft com dados (XDR) obsoletos.</span><span class="sxs-lookup"><span data-stu-id="3f175-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="3f175-109">A seguir está uma comparação entre a classe de <xref:System.Xml.Schema.XmlSchemaCollection> e a classe de <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="3f175-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="3f175-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="3f175-110">XmlSchemaCollection</span></span>|<span data-ttu-id="3f175-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3f175-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="3f175-112">Esquemas XML de XDR e o W3C da Microsoft de suporte.</span><span class="sxs-lookup"><span data-stu-id="3f175-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="3f175-113">Somente esquemas XML W3C de suporte.</span><span class="sxs-lookup"><span data-stu-id="3f175-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="3f175-114">Os esquemas são compilados quando o método de <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="3f175-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="3f175-115">Os esquemas não são compilados quando o método de <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="3f175-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="3f175-116">Isso fornece uma melhoria de desempenho durante a criação de biblioteca de esquema.</span><span class="sxs-lookup"><span data-stu-id="3f175-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="3f175-117">Cada esquema gerencia uma versão compilada individual que pode resultar de “para ilhas esquema.”</span><span class="sxs-lookup"><span data-stu-id="3f175-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="3f175-118">Como resultado, tudo inclui e importações são do escopo apenas dentro desse esquema.</span><span class="sxs-lookup"><span data-stu-id="3f175-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="3f175-119">Os esquemas compilados gerenciar um único esquema lógico, “set” de esquemas.</span><span class="sxs-lookup"><span data-stu-id="3f175-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="3f175-120">Todos os esquemas importados em um esquema que são adicionados ao dataset são adicionados diretamente ao conjunto próprios.</span><span class="sxs-lookup"><span data-stu-id="3f175-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="3f175-121">Isso significa que todos os tipos estão disponíveis para todos os esquemas.</span><span class="sxs-lookup"><span data-stu-id="3f175-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="3f175-122">Somente um esquema para um namespace de destino específico pode existir na coleção.</span><span class="sxs-lookup"><span data-stu-id="3f175-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="3f175-123">Vários esquemas para a mesma namespace de destino podem ser adicionados como não há nenhum conflito de tipo.</span><span class="sxs-lookup"><span data-stu-id="3f175-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="3f175-124">Migrar para o XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3f175-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="3f175-125">O exemplo de código fornece um guia para migrar para a nova classe de <xref:System.Xml.Schema.XmlSchemaSet> da classe obsoleta de <xref:System.Xml.Schema.XmlSchemaCollection> .</span><span class="sxs-lookup"><span data-stu-id="3f175-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="3f175-126">O exemplo de código a seguir ilustra as seguintes diferenças entre as duas classes.</span><span class="sxs-lookup"><span data-stu-id="3f175-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
-   <span data-ttu-id="3f175-127">Ao contrário do método de <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> da classe de <xref:System.Xml.Schema.XmlSchemaCollection> , os esquemas não são compilados ao chamar o método de <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-128">O método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de <xref:System.Xml.Schema.XmlSchemaSet> é chamado explicitamente no código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3f175-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
-   <span data-ttu-id="3f175-129">Para iterar sobre <xref:System.Xml.Schema.XmlSchemaSet>, você deve usar a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="3f175-130">A seguir está o exemplo de código obsoleto de <xref:System.Xml.Schema.XmlSchemaCollection> .</span><span class="sxs-lookup"><span data-stu-id="3f175-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="3f175-131">O exemplo a seguir é o equivalente de código de <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="3f175-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="3f175-132">Adicionando e recuperando esquemas</span><span class="sxs-lookup"><span data-stu-id="3f175-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="3f175-133">Os esquemas são adicionados a <xref:System.Xml.Schema.XmlSchemaSet> usando o método <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-134">Quando um esquema é adicionado a <xref:System.Xml.Schema.XmlSchemaSet>, está associado com o URI de um namespace de destino.</span><span class="sxs-lookup"><span data-stu-id="3f175-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="3f175-135">O URI de namespace de destino ou pode ser especificado como um parâmetro para o método de <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> ou se nenhuma namespace de destino for especificada, <xref:System.Xml.Schema.XmlSchemaSet> usa o namespace de destino definida no esquema.</span><span class="sxs-lookup"><span data-stu-id="3f175-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="3f175-136">Os esquemas são recuperados de <xref:System.Xml.Schema.XmlSchemaSet> usando a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-137">A propriedade de <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de <xref:System.Xml.Schema.XmlSchemaSet> permite que você faz iterações sobre os objetos de <xref:System.Xml.Schema.XmlSchema> contidos em <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-138">A propriedade de <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> retorna todos os objetos de <xref:System.Xml.Schema.XmlSchema> contidos em <xref:System.Xml.Schema.XmlSchemaSet>, ou, dado um parâmetro de namespace de destino, retorna todos os objetos de <xref:System.Xml.Schema.XmlSchema> que pertencem ao namespace de destino.</span><span class="sxs-lookup"><span data-stu-id="3f175-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="3f175-139">Se `null` é especificado como o parâmetro de namespace de destino, a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> retorna todos os esquemas sem um namespace.</span><span class="sxs-lookup"><span data-stu-id="3f175-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="3f175-140">O exemplo a seguir adiciona o esquema de `books.xsd` no espaço de `http://www.contoso.com/books` a <xref:System.Xml.Schema.XmlSchemaSet>, recupera todos os esquemas que pertencem ao namespace de `http://www.contoso.com/books` de <xref:System.Xml.Schema.XmlSchemaSet>, e grava os esquemas a <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="3f175-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="3f175-141">Para obter mais informações sobre como adicionar e recuperar esquemas de <xref:System.Xml.Schema.XmlSchemaSet> objeto, consulte o método de <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> e documentação de referência da propriedade de <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f175-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="3f175-142">Esquemas de compilação</span><span class="sxs-lookup"><span data-stu-id="3f175-142">Compiling Schemas</span></span>  
 <span data-ttu-id="3f175-143">Os esquemas em <xref:System.Xml.Schema.XmlSchemaSet> são compilados em um esquema lógico pelo método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f175-144">Ao contrário da classe obsoleta de <xref:System.Xml.Schema.XmlSchemaCollection> , os esquemas não são compilados quando o método de <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="3f175-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="3f175-145">Se o método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> executa com êxito, a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> de <xref:System.Xml.Schema.XmlSchemaSet> é definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="3f175-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f175-146">A propriedade de <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> não é afetado se os esquemas são editados quando em <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-147">As atualizações de esquemas individuais em <xref:System.Xml.Schema.XmlSchemaSet> não são controladas.</span><span class="sxs-lookup"><span data-stu-id="3f175-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="3f175-148">Como resultado, a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> pode ser `true` mesmo que um dos esquemas contidos em <xref:System.Xml.Schema.XmlSchemaSet> é modificado, como nenhum esquema foi adicionado ou removido de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="3f175-149">O exemplo a seguir adiciona o arquivo de `books.xsd` a <xref:System.Xml.Schema.XmlSchemaSet> e chama o método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f175-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="3f175-150">Para obter mais informações sobre esquemas de compilação em <xref:System.Xml.Schema.XmlSchemaSet>, consulte a documentação de referência de método <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f175-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="3f175-151">Reprocessamento esquemas</span><span class="sxs-lookup"><span data-stu-id="3f175-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="3f175-152">Reprocessamento um esquema em <xref:System.Xml.Schema.XmlSchemaSet> executa todas as etapas de pré-processamento executadas em um esquema quando o método de <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet> é chamado.</span><span class="sxs-lookup"><span data-stu-id="3f175-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="3f175-153">Se a chamada ao método de <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> for bem-sucedida, a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> de <xref:System.Xml.Schema.XmlSchemaSet> é definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="3f175-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="3f175-154">O método de <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> deve ser usado quando um esquema em <xref:System.Xml.Schema.XmlSchemaSet> foi alterado depois que <xref:System.Xml.Schema.XmlSchemaSet> executar a compilação.</span><span class="sxs-lookup"><span data-stu-id="3f175-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="3f175-155">O exemplo a seguir ilustra o reprocessamento um esquema adicionado a <xref:System.Xml.Schema.XmlSchemaSet> usando o método <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f175-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="3f175-156">Após <xref:System.Xml.Schema.XmlSchemaSet> é compilado usando o método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> , e o esquema adicionado a <xref:System.Xml.Schema.XmlSchemaSet> é alterado, a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> é definida como `true` mesmo que um esquema em <xref:System.Xml.Schema.XmlSchemaSet> é alterado.</span><span class="sxs-lookup"><span data-stu-id="3f175-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="3f175-157">Chamando o método <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> executa todo o pré-processamento executado pelo método de <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> , e defina a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="3f175-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="3f175-158">Para obter mais informações sobre reprocessamento de um esquema em <xref:System.Xml.Schema.XmlSchemaSet>, consulte a documentação de referência de método <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f175-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="3f175-159">Verificar se um esquema</span><span class="sxs-lookup"><span data-stu-id="3f175-159">Checking for a Schema</span></span>  
 <span data-ttu-id="3f175-160">Você pode usar o método de <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> de <xref:System.Xml.Schema.XmlSchemaSet> para verificar se um esquema está contido dentro de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-161">O método de <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> leva um namespace de destino ou um objeto de <xref:System.Xml.Schema.XmlSchema> para verificar.</span><span class="sxs-lookup"><span data-stu-id="3f175-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="3f175-162">Em ambos os casos, o método de <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> retorna `true` se o esquema está contido dentro de <xref:System.Xml.Schema.XmlSchemaSet>; caso contrário, retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="3f175-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="3f175-163">Para obter mais informações sobre como verificar para um esquema, consulte a documentação de referência de método <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f175-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="3f175-164">Removendo os esquemas</span><span class="sxs-lookup"><span data-stu-id="3f175-164">Removing Schemas</span></span>  
 <span data-ttu-id="3f175-165">Os esquemas são removidos de <xref:System.Xml.Schema.XmlSchemaSet> usando os métodos de <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> e de <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-166">O método de <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> remove o esquema especificado de <xref:System.Xml.Schema.XmlSchemaSet>, quando o método de <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> remover esquema especificado e todos os esquemas que importa de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="3f175-167">O exemplo a seguir ilustra adicionar vários esquemas a <xref:System.Xml.Schema.XmlSchemaSet>, então o uso do método de <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> para remover um de esquemas e todos os esquemas que importa.</span><span class="sxs-lookup"><span data-stu-id="3f175-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="3f175-168">Para obter mais informações sobre a remoção de esquemas de <xref:System.Xml.Schema.XmlSchemaSet>, consulte a documentação de referência dos métodos de <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> e de <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f175-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="3f175-169">Resolução e xs:importde esquema</span><span class="sxs-lookup"><span data-stu-id="3f175-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="3f175-170">Os exemplos a seguir descrevem comportamento de <xref:System.Xml.Schema.XmlSchemaSet> para importar esquemas quando vários esquemas para uma determinada namespace existem em <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="3f175-171">Por exemplo, considere <xref:System.Xml.Schema.XmlSchemaSet> que contém vários esquemas para o espaço de `http://www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="3f175-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="3f175-172">Um esquema com a seguinte diretiva de `xs:import` é adicionado a <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="3f175-173"><xref:System.Xml.Schema.XmlSchemaSet> tenta importar um esquema para o espaço de `http://www.contoso.com` carregar a URL de `http://www.contoso.com/schema.xsd` .</span><span class="sxs-lookup"><span data-stu-id="3f175-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="3f175-174">Somente a declaração e os tipos esquema declarados no documento de esquema estão disponíveis no esquema importando, mesmo que haja outros documentos de esquema para o espaço de `http://www.contoso.com` em <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-175">Se o arquivo de `schema.xsd` não pode ser localizado no URL de `http://www.contoso.com/schema.xsd` , nenhum esquema para o espaço de `http://www.contoso.com` é importado no esquema importando.</span><span class="sxs-lookup"><span data-stu-id="3f175-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="3f175-176">Validando documentos XML</span><span class="sxs-lookup"><span data-stu-id="3f175-176">Validating XML Documents</span></span>  
 <span data-ttu-id="3f175-177">Documentos XML podem ser validadas contra esquemas em <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="3f175-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f175-178">Você valide um documento XML adicionando um esquema para a propriedade de <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> de um objeto de <xref:System.Xml.XmlReaderSettings> , ou adicionando <xref:System.Xml.Schema.XmlSchemaSet> à propriedade de <xref:System.Xml.XmlReaderSettings.Schemas%2A> de um objeto de <xref:System.Xml.XmlReaderSettings> .</span><span class="sxs-lookup"><span data-stu-id="3f175-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="3f175-179">O objeto de <xref:System.Xml.XmlReaderSettings> é então usado pelo método de <xref:System.Xml.XmlReader.Create%2A> da classe de <xref:System.Xml.XmlReader> para criar um objeto de <xref:System.Xml.XmlReader> e para validar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="3f175-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="3f175-180">Para saber mais sobre como validar documentos XML usando um <xref:System.Xml.Schema.XmlSchemaSet>, confira [Validação de XSD (esquema XML) com XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="3f175-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f175-181">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f175-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
- [<span data-ttu-id="3f175-182">XmlSchemaSet como um cache de esquema</span><span class="sxs-lookup"><span data-stu-id="3f175-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [<span data-ttu-id="3f175-183">Validação de esquema XML (XSD) com XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3f175-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
