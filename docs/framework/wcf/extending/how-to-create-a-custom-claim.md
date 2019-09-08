---
title: 'Como: criar uma declaração personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 399aba1a6ad70ae37355f529a291ab2f604af03f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797083"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="95374-102">Como: criar uma declaração personalizada</span><span class="sxs-lookup"><span data-stu-id="95374-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="95374-103">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) fornece um conjunto de tipos de declaração internos e direitos com as funções auxiliares <xref:System.IdentityModel.Claims.Claim> para criar instâncias com esses tipos e direitos.</span><span class="sxs-lookup"><span data-stu-id="95374-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="95374-104">Essas declarações internas são projetadas para modelar informações encontradas nos tipos de credencial do cliente que o WCF dá suporte por padrão.</span><span class="sxs-lookup"><span data-stu-id="95374-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="95374-105">Em muitos casos, as declarações internas são suficientes; no entanto, alguns aplicativos podem exigir declarações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="95374-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="95374-106">Uma declaração consiste no tipo de declaração, o recurso ao qual a declaração se aplica e a direita que é declarada sobre esse recurso.</span><span class="sxs-lookup"><span data-stu-id="95374-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="95374-107">Este tópico descreve como criar uma declaração personalizada.</span><span class="sxs-lookup"><span data-stu-id="95374-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="95374-108">Para criar uma declaração personalizada baseada em um tipo de dados primitivo</span><span class="sxs-lookup"><span data-stu-id="95374-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="95374-109">Crie uma declaração personalizada passando o tipo de declaração, o valor do recurso e o <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> direito para o construtor.</span><span class="sxs-lookup"><span data-stu-id="95374-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="95374-110">Decida um valor exclusivo para o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="95374-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="95374-111">O tipo de declaração é um identificador de cadeia de caracteres exclusivo.</span><span class="sxs-lookup"><span data-stu-id="95374-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="95374-112">É responsabilidade do designer de declarações personalizado garantir que o identificador de cadeia de caracteres usado para o tipo de declaração seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="95374-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="95374-113">Para obter uma lista de tipos de declaração que são definidos pelo WCF, <xref:System.IdentityModel.Claims.ClaimTypes> consulte a classe.</span><span class="sxs-lookup"><span data-stu-id="95374-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="95374-114">Escolha o tipo de dados primitivo e o valor para o recurso.</span><span class="sxs-lookup"><span data-stu-id="95374-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="95374-115">Um recurso é um objeto.</span><span class="sxs-lookup"><span data-stu-id="95374-115">A resource is an object.</span></span> <span data-ttu-id="95374-116">O tipo CLR do recurso pode ser um primitivo, <xref:System.String> como ou <xref:System.Int32>ou qualquer tipo serializável.</span><span class="sxs-lookup"><span data-stu-id="95374-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="95374-117">O tipo CLR do recurso deve ser serializável, pois as declarações são serializadas em vários pontos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="95374-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="95374-118">Tipos primitivos são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="95374-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="95374-119">Escolha um direito que seja definido pelo WCF ou um valor exclusivo para um direito personalizado.</span><span class="sxs-lookup"><span data-stu-id="95374-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="95374-120">A direita é um identificador de cadeia de caracteres exclusivo.</span><span class="sxs-lookup"><span data-stu-id="95374-120">A right is a unique string identifier.</span></span> <span data-ttu-id="95374-121">Os direitos definidos pelo WCF são definidos na <xref:System.IdentityModel.Claims.Rights> classe.</span><span class="sxs-lookup"><span data-stu-id="95374-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="95374-122">É responsabilidade do designer de declarações personalizado garantir que o identificador de cadeia de caracteres usado para a direita seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="95374-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="95374-123">O exemplo de código a seguir cria uma declaração personalizada com um tipo `http://example.org/claims/simplecustomclaim`de declaração de, para `Driver's License`um recurso chamado e <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> com o direito.</span><span class="sxs-lookup"><span data-stu-id="95374-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="95374-124">Para criar uma declaração personalizada baseada em um tipo de dados não primitivo</span><span class="sxs-lookup"><span data-stu-id="95374-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="95374-125">Crie uma declaração personalizada passando o tipo de declaração, o valor do recurso e o <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> direito para o construtor.</span><span class="sxs-lookup"><span data-stu-id="95374-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="95374-126">Decida um valor exclusivo para o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="95374-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="95374-127">O tipo de declaração é um identificador de cadeia de caracteres exclusivo.</span><span class="sxs-lookup"><span data-stu-id="95374-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="95374-128">É responsabilidade do designer de declarações personalizado garantir que o identificador de cadeia de caracteres usado para o tipo de declaração seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="95374-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="95374-129">Para obter uma lista de tipos de declaração que são definidos pelo WCF, <xref:System.IdentityModel.Claims.ClaimTypes> consulte a classe.</span><span class="sxs-lookup"><span data-stu-id="95374-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="95374-130">Escolha ou defina um tipo não primitivo serializável para o recurso.</span><span class="sxs-lookup"><span data-stu-id="95374-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="95374-131">Um recurso é um objeto.</span><span class="sxs-lookup"><span data-stu-id="95374-131">A resource is an object.</span></span> <span data-ttu-id="95374-132">O tipo CLR do recurso deve ser serializável, pois as declarações são serializadas em vários pontos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="95374-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="95374-133">Tipos primitivos já são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="95374-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="95374-134">Quando um novo tipo é definido, aplique o <xref:System.Runtime.Serialization.DataContractAttribute> à classe.</span><span class="sxs-lookup"><span data-stu-id="95374-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="95374-135">Também aplique o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo a todos os membros do novo tipo que precisa ser serializado como parte da declaração.</span><span class="sxs-lookup"><span data-stu-id="95374-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="95374-136">O exemplo de código a seguir define um tipo de `MyResourceType`recurso personalizado chamado.</span><span class="sxs-lookup"><span data-stu-id="95374-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3. <span data-ttu-id="95374-137">Escolha um direito que seja definido pelo WCF ou um valor exclusivo para um direito personalizado.</span><span class="sxs-lookup"><span data-stu-id="95374-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="95374-138">A direita é um identificador de cadeia de caracteres exclusivo.</span><span class="sxs-lookup"><span data-stu-id="95374-138">A right is a unique string identifier.</span></span> <span data-ttu-id="95374-139">Os direitos definidos pelo WCF são definidos na <xref:System.IdentityModel.Claims.Rights> classe.</span><span class="sxs-lookup"><span data-stu-id="95374-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="95374-140">É responsabilidade do designer de declarações personalizado garantir que o identificador de cadeia de caracteres usado para a direita seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="95374-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="95374-141">O exemplo de código a seguir cria uma declaração personalizada com um tipo `http://example.org/claims/complexcustomclaim`de declaração de, um tipo `MyResourceType`de recurso personalizado de <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> e com a direita.</span><span class="sxs-lookup"><span data-stu-id="95374-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="95374-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95374-142">Example</span></span>  
 <span data-ttu-id="95374-143">O exemplo de código a seguir demonstra como criar uma declaração personalizada com um tipo de recurso primitivo e uma declaração personalizada com um tipo de recurso não primitivo.</span><span class="sxs-lookup"><span data-stu-id="95374-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="95374-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95374-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="95374-145">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="95374-145">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
