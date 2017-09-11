---
title: "Serialização e metadados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8da57c130f8b22a1e2de57678e86f84d00d11aaf
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="serialization-and-metadata"></a><span data-ttu-id="9ce27-102">Serialização e metadados</span><span class="sxs-lookup"><span data-stu-id="9ce27-102">Serialization and Metadata</span></span>
<span data-ttu-id="9ce27-103">Se seu aplicativo serializa ou desserializa objetos, talvez seja necessário adicionar entradas aos seus arquivos de diretivas de tempo de execução (.rd.xml) para garantir que os metadados necessários estejam presentes no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9ce27-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="9ce27-104">Há duas categorias de serializadores e cada uma necessita de um tratamento diferente no arquivo de diretivas de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="9ce27-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
-   <span data-ttu-id="9ce27-105">Serializadores de terceiros baseados em reflexão.</span><span class="sxs-lookup"><span data-stu-id="9ce27-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="9ce27-106">Eles necessitam de modificações no arquivo de diretivas de tempo de execução e são discutidos na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="9ce27-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
-   <span data-ttu-id="9ce27-107">Serializadores não baseados em reflexão localizados na Biblioteca de Classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ce27-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="9ce27-108">Eles podem necessitar de modificações no arquivo de diretivas de tempo de execução e são discutidos na seção [Serializadores da Microsoft](#Microsoft).</span><span class="sxs-lookup"><span data-stu-id="9ce27-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a><span data-ttu-id="9ce27-109">Serializadores de terceiros</span><span class="sxs-lookup"><span data-stu-id="9ce27-109">Third-party serializers</span></span>  
 <span data-ttu-id="9ce27-110">Serializadores de terceiros, incluindo o Newtonsoft.JSON, normalmente são baseadas em reflexão.</span><span class="sxs-lookup"><span data-stu-id="9ce27-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="9ce27-111">Dado um BLOB (objeto binário grande) de dados serializados, os campos nos dados são atribuídos a um tipo concreto examinando os campos do tipo de destino por nome.</span><span class="sxs-lookup"><span data-stu-id="9ce27-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="9ce27-112">No mínimo, usar essas bibliotecas causa exceções [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) para cada objeto <xref:System.Type> que você tentar serializar ou desserializar em uma coleção `List<Type>`.</span><span class="sxs-lookup"><span data-stu-id="9ce27-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="9ce27-113">A maneira mais fácil para solucionar problemas causados pela falta de metadados para esses serializadores é coletar tipos que serão usados na serialização de um único namespace (como `App.Models`) e aplicar uma diretiva de metadados `Serialize` a ele:</span><span class="sxs-lookup"><span data-stu-id="9ce27-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="9ce27-114">Para obter informações sobre a sintaxe usada no exemplo, consulte [Elemento \<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="9ce27-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a><span data-ttu-id="9ce27-115">Serializadores da Microsoft</span><span class="sxs-lookup"><span data-stu-id="9ce27-115">Microsoft serializers</span></span>  
 <span data-ttu-id="9ce27-116">Embora as classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer> não dependam de reflexão, elas necessitam que o código seja gerado com base no objeto a ser serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="9ce27-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="9ce27-117">Os construtores sobrecarregados para cada serializador incluem um parâmetro <xref:System.Type> que especifica o tipo a ser serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="9ce27-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="9ce27-118">A maneira como este tipo é especificado no código define a ação que deve ser tomada, conforme discutido nas duas próximas seções.</span><span class="sxs-lookup"><span data-stu-id="9ce27-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="9ce27-119">typeof usado no construtor</span><span class="sxs-lookup"><span data-stu-id="9ce27-119">typeof used in the constructor</span></span>  
 <span data-ttu-id="9ce27-120">Se você chamar um construtor dessas classes de serialização e incluir a palavra-chave de C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) na chamada do método, **não será necessário realizar qualquer trabalho adicional**.</span><span class="sxs-lookup"><span data-stu-id="9ce27-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="9ce27-121">Por exemplo, em cada uma das seguintes chamadas para um construtor de classe de serialização, a palavra-chave `typeof` é usada como parte da expressão passada para o construtor.</span><span class="sxs-lookup"><span data-stu-id="9ce27-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 <span data-ttu-id="9ce27-122">[!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]</span><span class="sxs-lookup"><span data-stu-id="9ce27-122">[!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]</span></span>  
  
 <span data-ttu-id="9ce27-123">O compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] lida automaticamente com esse código.</span><span class="sxs-lookup"><span data-stu-id="9ce27-123">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="9ce27-124">typeof usado fora do construtor</span><span class="sxs-lookup"><span data-stu-id="9ce27-124">typeof used outside the constructor</span></span>  
 <span data-ttu-id="9ce27-125">Se você chamar um construtor dessas classes de serialização e usar palavra-chave de C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) fora da expressão fornecida para o parâmetro <xref:System.Type> do construtor, como no código a seguir, o compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] não poderá resolver o tipo:</span><span class="sxs-lookup"><span data-stu-id="9ce27-125">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve the type:</span></span>  
  
 <span data-ttu-id="9ce27-126">[!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]</span><span class="sxs-lookup"><span data-stu-id="9ce27-126">[!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]</span></span>  
  
 <span data-ttu-id="9ce27-127">Nesse caso, você deve especificar o tipo do arquivo de diretivas de tempo de execução adicionando uma entrada como esta:</span><span class="sxs-lookup"><span data-stu-id="9ce27-127">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="9ce27-128">Da mesma forma, se você chamar um construtor como <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=fullName> e fornecer uma matriz de objetos <xref:System.Type> adicionais a serem serializados, como no código a seguir, o compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] não pode resolver esses tipos.</span><span class="sxs-lookup"><span data-stu-id="9ce27-128">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=fullName> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve these types.</span></span>  
  
 <span data-ttu-id="9ce27-129">[!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]</span><span class="sxs-lookup"><span data-stu-id="9ce27-129">[!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]</span></span>  
  
 <span data-ttu-id="9ce27-130">Você deve adicionar entradas como mostrado a seguir para cada tipo para o arquivo de diretivas de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="9ce27-130">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="9ce27-131">Para obter informações sobre a sintaxe usada no exemplo, consulte [Elemento \<Type>](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="9ce27-131">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce27-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ce27-132">See Also</span></span>  
 <span data-ttu-id="9ce27-133">[Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9ce27-133">[Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) </span></span>  
 <span data-ttu-id="9ce27-134">[Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md) </span><span class="sxs-lookup"><span data-stu-id="9ce27-134">[Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md) </span></span>  
 <span data-ttu-id="9ce27-135">[\<Elemento Type>](../../../docs/framework/net-native/type-element-net-native.md) </span><span class="sxs-lookup"><span data-stu-id="9ce27-135">[\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md) </span></span>  
 [<span data-ttu-id="9ce27-136">Elemento \<Namespace></span><span class="sxs-lookup"><span data-stu-id="9ce27-136">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)

