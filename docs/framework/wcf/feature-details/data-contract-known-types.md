---
title: Tipos de contratos de dados conhecidos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 2ab0a41e87a9b14d1beac9fb0c39586f0ea16a4a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040191"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="2b6fd-102">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="2b6fd-102">Data Contract Known Types</span></span>
<span data-ttu-id="2b6fd-103">A <xref:System.Runtime.Serialization.KnownTypeAttribute> classe permite que você especifique, com antecedência, os tipos que devem ser incluídos para consideração durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="2b6fd-104">Para obter um exemplo de trabalho, consulte o exemplo [tipos conhecidos](../../../../docs/framework/wcf/samples/known-types.md) .</span><span class="sxs-lookup"><span data-stu-id="2b6fd-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="2b6fd-105">Normalmente, ao passar parâmetros e retornar valores entre um cliente e um serviço, ambos os pontos de extremidade compartilham todos os contratos de dados dos dados a serem transmitidos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="2b6fd-106">No entanto, esse não é o caso nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="2b6fd-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="2b6fd-107">O contrato de dados enviado é derivado do contrato de dados esperado.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="2b6fd-108">Para obter mais informações, consulte a seção sobre herança em [equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span><span class="sxs-lookup"><span data-stu-id="2b6fd-108">For more information, see the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="2b6fd-109">Nesse caso, os dados transmitidos não têm o mesmo contrato de dados que o esperado pelo ponto de extremidade de recebimento.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="2b6fd-110">O tipo declarado para as informações a serem transmitidas é uma interface, em oposição a uma classe, estrutura ou enumeração.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="2b6fd-111">Portanto, não pode ser conhecido com antecedência qual tipo que implementa a interface é realmente enviado e, portanto, o ponto de extremidade de recebimento não pode determinar antecipadamente o contrato de dados para os dados transmitidos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="2b6fd-112">O tipo declarado para as informações a serem transmitidas <xref:System.Object>é.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="2b6fd-113">Como cada tipo é herdado de, e não pode ser conhecido com <xref:System.Object>antecedência qual tipo é realmente enviado, o ponto de extremidade de recebimento não pode determinar antecipadamente o contrato de dados para os dados transmitidos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="2b6fd-114">Este é um caso especial do primeiro item: Cada contrato de dados deriva do padrão, um contrato de dados em branco que é gerado <xref:System.Object>para o.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="2b6fd-115">Alguns tipos, que incluem tipos de .NET Framework, têm Membros que estão em uma das três categorias anteriores.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="2b6fd-116">Por exemplo, <xref:System.Collections.Hashtable> usa <xref:System.Object> para armazenar os objetos reais na tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="2b6fd-117">Ao serializar esses tipos, o lado de recebimento não pode determinar antecipadamente o contrato de dados para esses membros.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="2b6fd-118">A classe KnownTypeattribute</span><span class="sxs-lookup"><span data-stu-id="2b6fd-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="2b6fd-119">Quando os dados chegam em um ponto de extremidade de recebimento, o tempo de execução do WCF tenta desserializar os dados em uma instância de um tipo de Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2b6fd-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="2b6fd-120">O tipo instanciado para desserialização é escolhido primeiro inspecionando a mensagem de entrada para determinar o contrato de dados ao qual o conteúdo da mensagem está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="2b6fd-121">Em seguida, o mecanismo de desserialização tenta encontrar um tipo CLR que implementa um contrato de dados compatível com o conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="2b6fd-122">O conjunto de tipos candidatos que o mecanismo de desserialização permite durante esse processo é conhecido como o conjunto de "tipos conhecidos" do desserializador.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="2b6fd-123">Uma maneira de permitir que o mecanismo de desserialização saiba sobre um tipo é usando <xref:System.Runtime.Serialization.KnownTypeAttribute>o.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="2b6fd-124">O atributo não pode ser aplicado a membros de dados individuais, somente a tipos de contrato de dados inteiros.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="2b6fd-125">O atributo é aplicado a um *tipo externo* que pode ser uma classe ou uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="2b6fd-126">Em seu uso mais básico, a aplicação do atributo especifica um tipo como "tipo conhecido".</span><span class="sxs-lookup"><span data-stu-id="2b6fd-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="2b6fd-127">Isso faz com que o tipo conhecido seja uma parte do conjunto de tipos conhecidos sempre que um objeto do tipo externo ou qualquer objeto referido por seus membros está sendo desserializado.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="2b6fd-128">Mais de um <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo pode ser aplicado ao mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="2b6fd-129">Tipos conhecidos e primitivos</span><span class="sxs-lookup"><span data-stu-id="2b6fd-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="2b6fd-130">Tipos primitivos, bem como determinados tipos tratados como primitivos (por exemplo, <xref:System.DateTime> e <xref:System.Xml.XmlElement>) são sempre "conhecidos" e nunca precisam ser adicionados por meio desse mecanismo.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="2b6fd-131">No entanto, as matrizes de tipos primitivos precisam ser adicionadas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="2b6fd-132">A maioria das coleções é considerada equivalente a matrizes.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="2b6fd-133">(As coleções não genéricas são consideradas equivalentes a matrizes de <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="2b6fd-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="2b6fd-134">Para obter um exemplo de como usar primitivas, matrizes primitivas e coleções primitivas, consulte o exemplo 4.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b6fd-135">Ao contrário de outros tipos primitivos, a <xref:System.DateTimeOffset> estrutura não é um tipo conhecido por padrão, portanto, ela deve ser adicionada manualmente à lista de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2b6fd-136">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2b6fd-136">Examples</span></span>  
 <span data-ttu-id="2b6fd-137">Os exemplos a seguir mostram <xref:System.Runtime.Serialization.KnownTypeAttribute> a classe em uso.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="2b6fd-138">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="2b6fd-138">Example 1</span></span>  
 <span data-ttu-id="2b6fd-139">Há três classes com uma relação de herança.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="2b6fd-140">A classe `CompanyLogo` a seguir pode ser serializada, mas não poderá ser desserializada se o `ShapeOfLogo` membro for definido `CircleType` como um `TriangleType` ou um objeto, porque o mecanismo de desserialização não reconhece nenhum tipo com nomes de contrato de dados " Circle "ou" triângulo ".</span><span class="sxs-lookup"><span data-stu-id="2b6fd-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="2b6fd-141">A maneira correta de gravar o `CompanyLogo` tipo é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="2b6fd-142">Sempre que o tipo `CompanyLogo2` externo está sendo desserializado, o mecanismo de desserialização `CircleType` sabe `TriangleType` e e, portanto, é capaz de encontrar tipos correspondentes para os contratos de dados "Circle" e "triângulo".</span><span class="sxs-lookup"><span data-stu-id="2b6fd-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="2b6fd-143">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="2b6fd-143">Example 2</span></span>  
 <span data-ttu-id="2b6fd-144">No exemplo `CustomerTypeA` a seguir, embora o e `CustomerTypeB` o tenham o `Customer` contrato de dados, uma instância `CustomerTypeB` do é criada sempre `PurchaseOrder` que um é desserializado, `CustomerTypeB` porque apenas é conhecido pelo mecanismo de desserialização.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="2b6fd-145">Exemplo 3:</span><span class="sxs-lookup"><span data-stu-id="2b6fd-145">Example 3</span></span>  
 <span data-ttu-id="2b6fd-146">No exemplo a seguir, um <xref:System.Collections.Hashtable> armazena seu conteúdo internamente como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="2b6fd-147">Para desserializar uma tabela de hash com êxito, o mecanismo de desserialização deve saber o conjunto de possíveis tipos que podem ocorrer lá.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="2b6fd-148">Nesse caso, sabemos com antecedência `Book` que somente os `Catalog`objetos e `Magazine` são armazenados no, portanto, eles são adicionados usando o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="2b6fd-149">Exemplo 4</span><span class="sxs-lookup"><span data-stu-id="2b6fd-149">Example 4</span></span>  
 <span data-ttu-id="2b6fd-150">No exemplo a seguir, um contrato de dados armazena um número e uma operação a ser executada no número.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="2b6fd-151">O `Numbers` membro de dados pode ser um inteiro, uma matriz de inteiros ou um <xref:System.Collections.Generic.List%601> que contenha inteiros.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2b6fd-152">Isso só funcionará no lado do cliente se SVCUTIL. EXE é usado para gerar um proxy WCF.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="2b6fd-153">SVCUTIL. EXE recupera os metadados do serviço, incluindo todos os tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="2b6fd-154">Sem essas informações, um cliente não poderá desserializar os tipos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="2b6fd-155">Este é o código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="2b6fd-156">Tipos, herança e interfaces conhecidos</span><span class="sxs-lookup"><span data-stu-id="2b6fd-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="2b6fd-157">Quando um tipo conhecido é associado a um tipo específico usando o `KnownTypeAttribute` atributo, o tipo conhecido também é associado a todos os tipos derivados desse tipo.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="2b6fd-158">Por exemplo, consulte o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="2b6fd-159">A `DoubleDrawing` classe não requer o `KnownTypeAttribute` atributo `Square` `Circle` aser`Drawing`usado e, no campo,porqueaclassebase()játemessesatributosaplicados.`AdditionalShape`</span><span class="sxs-lookup"><span data-stu-id="2b6fd-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="2b6fd-160">Tipos conhecidos podem ser associados somente a classes e estruturas, não a interfaces.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="2b6fd-161">Tipos conhecidos usando métodos genéricos abertos</span><span class="sxs-lookup"><span data-stu-id="2b6fd-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="2b6fd-162">Pode ser necessário adicionar um tipo genérico como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="2b6fd-163">No entanto, um tipo genérico aberto não pode ser passado como um `KnownTypeAttribute` parâmetro para o atributo.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="2b6fd-164">Esse problema pode ser resolvido usando um mecanismo alternativo: Escreva um método que retorne uma lista de tipos a serem adicionados à coleção de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="2b6fd-165">O nome do método é especificado como um argumento de cadeia de caracteres para `KnownTypeAttribute` o atributo devido a algumas restrições.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="2b6fd-166">O método deve existir no tipo ao qual o `KnownTypeAttribute` atributo é aplicado, deve ser estático, não deve aceitar nenhum parâmetro e deve retornar um objeto que possa ser atribuído a <xref:System.Collections.IEnumerable> de <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="2b6fd-167">Você não pode combinar `KnownTypeAttribute` o atributo com um nome de `KnownTypeAttribute` método e atributos com tipos reais no mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="2b6fd-168">Além disso, você não pode aplicar mais `KnownTypeAttribute` de um com um nome de método ao mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="2b6fd-169">Consulte a classe a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="2b6fd-170">O `theDrawing` campo contém instâncias de uma classe `ColorDrawing` genérica e uma classe `BlackAndWhiteDrawing`genérica, ambas herdadas de uma classe `Drawing`genérica.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="2b6fd-171">Normalmente, ambos devem ser adicionados a tipos conhecidos, mas a sintaxe a seguir não é válida para atributos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="2b6fd-172">Portanto, um método deve ser criado para retornar esses tipos.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="2b6fd-173">A maneira correta de escrever esse tipo, em seguida, é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="2b6fd-174">Outras maneiras de adicionar tipos conhecidos</span><span class="sxs-lookup"><span data-stu-id="2b6fd-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="2b6fd-175">Além disso, tipos conhecidos podem ser adicionados por meio de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="2b6fd-176">Isso é útil quando você não controla o tipo que requer tipos conhecidos para desserialização adequada, como ao usar bibliotecas de tipo de terceiros com o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2b6fd-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="2b6fd-177">O arquivo de configuração a seguir mostra como especificar um tipo conhecido em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="2b6fd-178">No arquivo de configuração anterior, um tipo de contrato `MyCompany.Library.Shape` de dados chamado é `MyCompany.Library.Circle` declarado como tendo um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="2b6fd-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6fd-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b6fd-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="2b6fd-180">Tipos conhecidos</span><span class="sxs-lookup"><span data-stu-id="2b6fd-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)
- [<span data-ttu-id="2b6fd-181">Equivalência de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="2b6fd-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="2b6fd-182">Criando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="2b6fd-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
