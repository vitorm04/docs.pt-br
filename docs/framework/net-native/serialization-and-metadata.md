---
title: Serialização e metadados
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: cc9adf0e6627ef3190e74fea5d4f0f3afd581811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81389230"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="9039e-102">Serialização e metadados</span><span class="sxs-lookup"><span data-stu-id="9039e-102">Serialization and Metadata</span></span>

<span data-ttu-id="9039e-103">Se seu aplicativo serializa ou desserializa objetos, talvez seja necessário adicionar entradas aos seus arquivos de diretivas de runtime (.rd.xml) para garantir que os metadados necessários estejam presentes no runtime.</span><span class="sxs-lookup"><span data-stu-id="9039e-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="9039e-104">Há duas categorias de serializadores e cada uma necessita de um tratamento diferente no arquivo de diretivas de runtime:</span><span class="sxs-lookup"><span data-stu-id="9039e-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="9039e-105">Serializadores de terceiros baseados em reflexão.</span><span class="sxs-lookup"><span data-stu-id="9039e-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="9039e-106">Eles necessitam de modificações no arquivo de diretivas de runtime e são discutidos na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="9039e-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="9039e-107">Serializadores não baseados em reflexão encontrados na biblioteca de classes de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9039e-107">Non-reflection-based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="9039e-108">Eles podem necessitar de modificações no arquivo de diretivas de runtime e são discutidos na seção [Serializadores da Microsoft](#Microsoft).</span><span class="sxs-lookup"><span data-stu-id="9039e-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="9039e-109">Serializadores de terceiros</span><span class="sxs-lookup"><span data-stu-id="9039e-109">Third-party serializers</span></span>

 <span data-ttu-id="9039e-110">Serializadores de terceiros, incluindo o Newtonsoft.JSON, normalmente são baseadas em reflexão.</span><span class="sxs-lookup"><span data-stu-id="9039e-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="9039e-111">Dado um BLOB (objeto binário grande) de dados serializados, os campos nos dados são atribuídos a um tipo concreto examinando os campos do tipo de destino por nome.</span><span class="sxs-lookup"><span data-stu-id="9039e-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="9039e-112">No mínimo, usar essas bibliotecas causa exceções [MissingMetadataException](missingmetadataexception-class-net-native.md) para cada objeto <xref:System.Type> que você tentar serializar ou desserializar em uma coleção `List<Type>`.</span><span class="sxs-lookup"><span data-stu-id="9039e-112">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="9039e-113">A maneira mais fácil para solucionar problemas causados pela falta de metadados para esses serializadores é coletar tipos que serão usados na serialização de um único namespace (como `App.Models`) e aplicar uma diretiva de metadados `Serialize` a ele:</span><span class="sxs-lookup"><span data-stu-id="9039e-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="9039e-114">Para obter informações sobre a sintaxe usada no exemplo, consulte [ \<Namespace> elemento](namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="9039e-114">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="9039e-115">Serializadores da Microsoft</span><span class="sxs-lookup"><span data-stu-id="9039e-115">Microsoft serializers</span></span>

 <span data-ttu-id="9039e-116">Embora as classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer> não dependam de reflexão, elas necessitam que o código seja gerado com base no objeto a ser serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="9039e-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="9039e-117">Os construtores sobrecarregados para cada serializador incluem um parâmetro <xref:System.Type> que especifica o tipo a ser serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="9039e-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="9039e-118">A maneira como este tipo é especificado no código define a ação que deve ser tomada, conforme discutido nas duas próximas seções.</span><span class="sxs-lookup"><span data-stu-id="9039e-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="9039e-119">typeof usado no construtor</span><span class="sxs-lookup"><span data-stu-id="9039e-119">typeof used in the constructor</span></span>

 <span data-ttu-id="9039e-120">Se você chamar um construtor dessas classes de serialização e incluir o operador [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) do C# na chamada do método, **não será necessário fazer nenhum trabalho adicional**.</span><span class="sxs-lookup"><span data-stu-id="9039e-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="9039e-121">Por exemplo, em cada uma das seguintes chamadas para um construtor de classe de serialização, a palavra-chave `typeof` é usada como parte da expressão passada para o construtor.</span><span class="sxs-lookup"><span data-stu-id="9039e-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="9039e-122">O compilador de .NET Native tratará automaticamente esse código.</span><span class="sxs-lookup"><span data-stu-id="9039e-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="9039e-123">typeof usado fora do construtor</span><span class="sxs-lookup"><span data-stu-id="9039e-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="9039e-124">Se você chamar um construtor dessas classes de serialização e usar o operador [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) do C# fora da expressão fornecida ao parâmetro do construtor <xref:System.Type> , como no código a seguir, o compilador .net Native não poderá resolver o tipo:</span><span class="sxs-lookup"><span data-stu-id="9039e-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="9039e-125">Nesse caso, você deve especificar o tipo do arquivo de diretivas de runtime adicionando uma entrada como esta:</span><span class="sxs-lookup"><span data-stu-id="9039e-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="9039e-126">Da mesma forma, se você chamar um construtor como <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> e fornecer uma matriz de <xref:System.Type> objetos adicionais para serializar, como no código a seguir, o compilador .net Native não poderá resolver esses tipos.</span><span class="sxs-lookup"><span data-stu-id="9039e-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
<span data-ttu-id="9039e-127">Adicione entradas como as seguintes para cada tipo para o arquivo de diretivas de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="9039e-127">Add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
<span data-ttu-id="9039e-128">Para obter informações sobre a sintaxe usada no exemplo, consulte [ \<Type> elemento](type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="9039e-128">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9039e-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="9039e-129">See also</span></span>

- [<span data-ttu-id="9039e-130">Referência do arquivo de configuração de diretivas do runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9039e-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9039e-131">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="9039e-131">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9039e-132">\<Type>Elementos</span><span class="sxs-lookup"><span data-stu-id="9039e-132">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="9039e-133">\<Namespace>Elementos</span><span class="sxs-lookup"><span data-stu-id="9039e-133">\<Namespace> Element</span></span>](namespace-element-net-native.md)
