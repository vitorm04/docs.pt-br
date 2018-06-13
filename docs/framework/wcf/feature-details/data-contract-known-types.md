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
ms.openlocfilehash: 00ae32ff394b1ce2acb38fb237527e934934b935
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496003"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="ee130-102">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="ee130-102">Data Contract Known Types</span></span>
<span data-ttu-id="ee130-103">O <xref:System.Runtime.Serialization.KnownTypeAttribute> classe permite que você especificar com antecedência, os tipos que devem ser incluídos para consideração durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="ee130-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="ee130-104">Para obter um exemplo de funcionamento, consulte o [tipos conhecidos](../../../../docs/framework/wcf/samples/known-types.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="ee130-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="ee130-105">Normalmente, ao passar parâmetros e valores de retorno entre um cliente e um serviço, ambos os pontos de extremidade compartilham todos os contratos de dados dos dados a serem transmitidos.</span><span class="sxs-lookup"><span data-stu-id="ee130-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="ee130-106">No entanto, isso não for o caso nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="ee130-106">However, this is not the case in the following circumstances:</span></span>  
  
-   <span data-ttu-id="ee130-107">O contrato de dados enviados é derivado do contrato de dados esperado.</span><span class="sxs-lookup"><span data-stu-id="ee130-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="ee130-108">Para obter mais informações, consulte a seção sobre a herança em [equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span><span class="sxs-lookup"><span data-stu-id="ee130-108">For more information, see the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="ee130-109">Nesse caso, os dados transmitidos não tem os mesmos dados conforme o esperado pelo ponto de extremidade de recebimento do contrato.</span><span class="sxs-lookup"><span data-stu-id="ee130-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
-   <span data-ttu-id="ee130-110">O tipo declarado para as informações a serem transmitidos é uma interface, em vez de uma classe, estrutura ou enumeração.</span><span class="sxs-lookup"><span data-stu-id="ee130-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="ee130-111">Portanto, ele não pode ser conhecido com antecedência qual o tipo que implementa a interface é enviada e, portanto, o ponto de extremidade de recebimento não pode determinar antecipadamente o contrato de dados para os dados transmitidos.</span><span class="sxs-lookup"><span data-stu-id="ee130-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
-   <span data-ttu-id="ee130-112">O tipo declarado para as informações a serem transmitidos é <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="ee130-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="ee130-113">Como cada tipo herda de <xref:System.Object>e ele não pode ser conhecido com antecedência qual tipo é realmente enviado, o ponto de extremidade de recebimento não pode determinar antecipadamente o contrato de dados para os dados transmitidos.</span><span class="sxs-lookup"><span data-stu-id="ee130-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="ee130-114">Esse é um caso especial do primeiro item: cada contrato de dados é derivado do padrão, um contrato de dados em branco que é gerado para <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="ee130-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="ee130-115">Alguns tipos, que incluem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos, têm membros que estão em uma das três categorias a anterior.</span><span class="sxs-lookup"><span data-stu-id="ee130-115">Some types, which include [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="ee130-116">Por exemplo, <xref:System.Collections.Hashtable> usa <xref:System.Object> para armazenar os objetos reais na tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="ee130-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="ee130-117">Ao serializar desses tipos, o lado de recebimento não pode determinar antecipadamente o contrato de dados para esses membros.</span><span class="sxs-lookup"><span data-stu-id="ee130-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="ee130-118">A classe KnownTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="ee130-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="ee130-119">Quando os dados chegam a um ponto de extremidade de recebimento, o tempo de execução WCF tenta desserializar os dados em uma instância de um tipo do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ee130-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="ee130-120">O tipo é instanciado para desserialização é escolhido inspecionando primeiro contrato que o conteúdo da mensagem está de acordo com a mensagem de entrada para determinar os dados.</span><span class="sxs-lookup"><span data-stu-id="ee130-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="ee130-121">O mecanismo de desserialização, em seguida, tenta encontrar um tipo CLR que implementa um contrato de dados compatível com o conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ee130-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="ee130-122">O conjunto de tipos de candidato que permite que o mecanismo de desserialização para durante esse processo é chamado de conjunto do desserializador de "tipos conhecidos".</span><span class="sxs-lookup"><span data-stu-id="ee130-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="ee130-123">Uma maneira de permitir que o mecanismo de desserialização saibam sobre um tipo é usando o <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ee130-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="ee130-124">O atributo não pode ser aplicado a membros de dados individuais, somente aos tipos de contrato de dados inteiro.</span><span class="sxs-lookup"><span data-stu-id="ee130-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="ee130-125">O atributo é aplicado a um *tipo externo* que pode ser uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee130-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="ee130-126">Em seu uso mais básico, aplicando o atributo especifica um tipo como um "tipo conhecido".</span><span class="sxs-lookup"><span data-stu-id="ee130-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="ee130-127">Isso faz com que o tipo conhecido ser parte do conjunto de tipos conhecidos sempre que um objeto do tipo externo ou qualquer objeto referenciado por meio de seus membros está sendo desserializado.</span><span class="sxs-lookup"><span data-stu-id="ee130-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="ee130-128">Mais de um <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo pode ser aplicado para o mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="ee130-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="ee130-129">Tipos primitivos e tipos conhecidos</span><span class="sxs-lookup"><span data-stu-id="ee130-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="ee130-130">Tipos primitivos, bem como alguns tipos são tratadas como tipos primitivos (por exemplo, <xref:System.DateTime> e <xref:System.Xml.XmlElement>) são sempre "é conhecido" e nunca devem ser adicionados por meio desse mecanismo.</span><span class="sxs-lookup"><span data-stu-id="ee130-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="ee130-131">No entanto, matrizes de tipos primitivos precisam ser adicionados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="ee130-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="ee130-132">A maioria das coleções são consideradas equivalentes às matrizes.</span><span class="sxs-lookup"><span data-stu-id="ee130-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="ee130-133">(Coleções não genéricas são consideradas equivalentes a matrizes de <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="ee130-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="ee130-134">Para obter um exemplo de como o usar tipos primitivos, matrizes primitivas e coleções primitivo, consulte o exemplo 4.</span><span class="sxs-lookup"><span data-stu-id="ee130-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee130-135">Ao contrário de outros tipos primitivos, de <xref:System.DateTimeOffset> estrutura não é um tipo conhecido por padrão, portanto, devem ser adicionada manualmente à lista de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="ee130-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ee130-136">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ee130-136">Examples</span></span>  
 <span data-ttu-id="ee130-137">Os exemplos a seguir mostram o <xref:System.Runtime.Serialization.KnownTypeAttribute> classe em uso.</span><span class="sxs-lookup"><span data-stu-id="ee130-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="ee130-138">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="ee130-138">Example 1</span></span>  
 <span data-ttu-id="ee130-139">Há três classes com uma relação de herança.</span><span class="sxs-lookup"><span data-stu-id="ee130-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="ee130-140">O seguinte `CompanyLogo` classe pode ser serializada, mas não pode ser desserializado se o `ShapeOfLogo` membro é definido como um `CircleType` ou um `TriangleType` objeto, pois o mecanismo de desserialização não reconhece qualquer tipo com nomes de contrato de dados " Círculo"ou"Triângulo".</span><span class="sxs-lookup"><span data-stu-id="ee130-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="ee130-141">A maneira correta de gravar o `CompanyLogo` tipo é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee130-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="ee130-142">Sempre que o tipo externo `CompanyLogo2` está sendo desserializado, o mecanismo de desserialização conhece `CircleType` e `TriangleType` e, portanto, é possível localizar tipos de correspondência para os contratos de dados "Círculo" e "Triângulo".</span><span class="sxs-lookup"><span data-stu-id="ee130-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="ee130-143">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="ee130-143">Example 2</span></span>  
 <span data-ttu-id="ee130-144">No exemplo a seguir, mesmo que ambos `CustomerTypeA` e `CustomerTypeB` tem o `Customer` de contrato de dados, uma instância do `CustomerTypeB` é criado sempre que um `PurchaseOrder` é desserializado, pois apenas `CustomerTypeB` é conhecido para o mecanismo de desserialização.</span><span class="sxs-lookup"><span data-stu-id="ee130-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="ee130-145">Exemplo 3:</span><span class="sxs-lookup"><span data-stu-id="ee130-145">Example 3</span></span>  
 <span data-ttu-id="ee130-146">No exemplo a seguir, uma <xref:System.Collections.Hashtable> armazena seu conteúdo internamente como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="ee130-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="ee130-147">Para desserializar a uma tabela de hash com êxito, o mecanismo de desserialização deve saber o conjunto de possíveis tipos que podem ocorrer existe.</span><span class="sxs-lookup"><span data-stu-id="ee130-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="ee130-148">Nesse caso, estamos saber com antecedência que apenas `Book` e `Magazine` são armazenados no `Catalog`, portanto, aqueles são adicionados usando o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="ee130-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="ee130-149">Exemplo 4</span><span class="sxs-lookup"><span data-stu-id="ee130-149">Example 4</span></span>  
 <span data-ttu-id="ee130-150">No exemplo a seguir, um contrato de dados armazena um número e uma operação para executar o número.</span><span class="sxs-lookup"><span data-stu-id="ee130-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="ee130-151">O `Numbers` membro de dados pode ser um inteiro, uma matriz de inteiros, ou um <xref:System.Collections.Generic.List%601> que contém números inteiros.</span><span class="sxs-lookup"><span data-stu-id="ee130-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ee130-152">Isso só funcionará no lado do cliente se SVCUTIL. EXE é usado para gerar um proxy do WCF.</span><span class="sxs-lookup"><span data-stu-id="ee130-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="ee130-153">SVCUTIL. EXE recupera metadados do serviço, incluindo quaisquer tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="ee130-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="ee130-154">Sem essas informações um cliente não poderá desserializar os tipos.</span><span class="sxs-lookup"><span data-stu-id="ee130-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="ee130-155">Este é o código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee130-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="ee130-156">Interfaces e herança de tipos conhecidos</span><span class="sxs-lookup"><span data-stu-id="ee130-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="ee130-157">Quando um tipo conhecido é associado a um tipo específico usando o `KnownTypeAttribute` atributo, o tipo conhecido também é associado a todos os tipos derivados do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="ee130-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="ee130-158">Por exemplo, consulte o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee130-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="ee130-159">O `DoubleDrawing` classe não requer o `KnownTypeAttribute` atributo usar `Square` e `Circle` no `AdditionalShape` campo, porque a classe base (`Drawing`) já tem estes atributos aplicados.</span><span class="sxs-lookup"><span data-stu-id="ee130-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="ee130-160">Tipos conhecidos podem ser associados somente classes e estruturas, interfaces não.</span><span class="sxs-lookup"><span data-stu-id="ee130-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="ee130-161">Tipos conhecidos usando métodos genéricos abertos</span><span class="sxs-lookup"><span data-stu-id="ee130-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="ee130-162">Pode ser necessário adicionar um tipo genérico como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="ee130-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="ee130-163">No entanto, um tipo genérico aberto não pode ser passado como um parâmetro para o `KnownTypeAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="ee130-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="ee130-164">Esse problema pode ser resolvido por meio de um mecanismo alternativo: escrever um método que retorna uma lista de tipos a serem adicionados à coleção de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="ee130-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="ee130-165">O nome do método é especificado então como um argumento de cadeia de caracteres para o `KnownTypeAttribute` atributo devido a algumas restrições.</span><span class="sxs-lookup"><span data-stu-id="ee130-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="ee130-166">O método deve existir no tipo ao qual o `KnownTypeAttribute` atributo é aplicado, deve ser estático, não deve aceitar nenhum parâmetro e deve retornar um objeto que pode ser atribuído a <xref:System.Collections.IEnumerable> de <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="ee130-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="ee130-167">Não é possível combinar o `KnownTypeAttribute` atributo com um nome de método e `KnownTypeAttribute` atributos com tipos reais do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="ee130-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="ee130-168">Além disso, você não pode aplicar mais de um `KnownTypeAttribute` com um nome de método para o mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="ee130-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="ee130-169">Consulte a seguinte classe.</span><span class="sxs-lookup"><span data-stu-id="ee130-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="ee130-170">O `theDrawing` campo contém instâncias de uma classe genérica `ColorDrawing` e uma classe genérica `BlackAndWhiteDrawing`, que herdam de uma classe genérica `Drawing`.</span><span class="sxs-lookup"><span data-stu-id="ee130-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="ee130-171">Normalmente, ambos devem ser adicionadas aos tipos conhecidos, mas a seguir não é uma sintaxe válida para os atributos.</span><span class="sxs-lookup"><span data-stu-id="ee130-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="ee130-172">Assim, um método deve ser criado para esses tipos de retorno.</span><span class="sxs-lookup"><span data-stu-id="ee130-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="ee130-173">A maneira correta de gravar este tipo, em seguida, é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee130-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="ee130-174">Outras maneiras de adicionar tipos conhecidos</span><span class="sxs-lookup"><span data-stu-id="ee130-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="ee130-175">Além disso, os tipos conhecidos podem ser adicionados por meio de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ee130-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="ee130-176">Isso é útil quando você não controla o tipo que requer tipos conhecidos para desserialização apropriada, como quando usando produtos de terceiros com o Windows Communication Foundation (WCF) de bibliotecas de tipos.</span><span class="sxs-lookup"><span data-stu-id="ee130-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="ee130-177">O arquivo de configuração a seguir mostra como especificar um tipo conhecido em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ee130-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="ee130-178">Na configuração anterior de um tipo de contrato de dados chamado arquivo `MyCompany.Library.Shape` é declarada com `MyCompany.Library.Circle` como um tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="ee130-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee130-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee130-179">See Also</span></span>  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Object>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>  
 [<span data-ttu-id="ee130-180">Tipos conhecidos</span><span class="sxs-lookup"><span data-stu-id="ee130-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)  
 [<span data-ttu-id="ee130-181">Equivalência de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="ee130-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="ee130-182">Criando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="ee130-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
