---
title: Como criar uma afirmação personalizada
description: Saiba como criar uma declaração personalizada no WCF. O WCF dá suporte a uma variedade de declarações internas e alguns aplicativos podem exigir declarações personalizadas.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 89f2b1359b48b71720db6ff38f27883745cfe612
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247540"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="1baf0-104">Como criar uma afirmação personalizada</span><span class="sxs-lookup"><span data-stu-id="1baf0-104">How to: Create a Custom Claim</span></span>
<span data-ttu-id="1baf0-105">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) fornece um conjunto de tipos de declaração internos e direitos com as funções auxiliares para criar <xref:System.IdentityModel.Claims.Claim> instâncias com esses tipos e direitos.</span><span class="sxs-lookup"><span data-stu-id="1baf0-105">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="1baf0-106">Essas declarações internas são projetadas para modelar informações encontradas nos tipos de credencial do cliente que o WCF dá suporte por padrão.</span><span class="sxs-lookup"><span data-stu-id="1baf0-106">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="1baf0-107">Em muitos casos, as declarações internas são suficientes; no entanto, alguns aplicativos podem exigir declarações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="1baf0-107">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="1baf0-108">Uma declaração consiste no tipo de declaração, o recurso ao qual a declaração se aplica e a direita que é declarada sobre esse recurso.</span><span class="sxs-lookup"><span data-stu-id="1baf0-108">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="1baf0-109">Este tópico descreve como criar uma declaração personalizada.</span><span class="sxs-lookup"><span data-stu-id="1baf0-109">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="1baf0-110">Para criar uma declaração personalizada baseada em um tipo de dados primitivo</span><span class="sxs-lookup"><span data-stu-id="1baf0-110">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="1baf0-111">Crie uma declaração personalizada passando o tipo de declaração, o valor do recurso e o direito para o <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Construtor.</span><span class="sxs-lookup"><span data-stu-id="1baf0-111">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="1baf0-112">Decida um valor exclusivo para o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="1baf0-112">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="1baf0-113">O tipo de declaração é um identificador de cadeia de caracteres exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-113">The claim type is a unique string identifier.</span></span> <span data-ttu-id="1baf0-114">É responsabilidade do designer de declarações personalizado garantir que o identificador de cadeia de caracteres usado para o tipo de declaração seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-114">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="1baf0-115">Para obter uma lista de tipos de declaração que são definidos pelo WCF, consulte a <xref:System.IdentityModel.Claims.ClaimTypes> classe.</span><span class="sxs-lookup"><span data-stu-id="1baf0-115">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="1baf0-116">Escolha o tipo de dados primitivo e o valor para o recurso.</span><span class="sxs-lookup"><span data-stu-id="1baf0-116">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="1baf0-117">Um recurso é um objeto.</span><span class="sxs-lookup"><span data-stu-id="1baf0-117">A resource is an object.</span></span> <span data-ttu-id="1baf0-118">O tipo CLR do recurso pode ser um primitivo, como ou ou <xref:System.String> <xref:System.Int32> qualquer tipo serializável.</span><span class="sxs-lookup"><span data-stu-id="1baf0-118">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="1baf0-119">O tipo CLR do recurso deve ser serializável, pois as declarações são serializadas em vários pontos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="1baf0-119">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="1baf0-120">Tipos primitivos são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="1baf0-120">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="1baf0-121">Escolha um direito que seja definido pelo WCF ou um valor exclusivo para um direito personalizado.</span><span class="sxs-lookup"><span data-stu-id="1baf0-121">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="1baf0-122">A direita é um identificador de cadeia de caracteres exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-122">A right is a unique string identifier.</span></span> <span data-ttu-id="1baf0-123">Os direitos definidos pelo WCF são definidos na <xref:System.IdentityModel.Claims.Rights> classe.</span><span class="sxs-lookup"><span data-stu-id="1baf0-123">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="1baf0-124">É responsabilidade do designer de declarações personalizado garantir que o identificador de cadeia de caracteres usado para a direita seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-124">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="1baf0-125">O exemplo de código a seguir cria uma declaração personalizada com um tipo de declaração de `http://example.org/claims/simplecustomclaim` , para um recurso chamado `Driver's License` e com o <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> direito.</span><span class="sxs-lookup"><span data-stu-id="1baf0-125">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="1baf0-126">Para criar uma declaração personalizada baseada em um tipo de dados não primitivo</span><span class="sxs-lookup"><span data-stu-id="1baf0-126">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="1baf0-127">Crie uma declaração personalizada passando o tipo de declaração, o valor do recurso e o direito para o <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Construtor.</span><span class="sxs-lookup"><span data-stu-id="1baf0-127">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="1baf0-128">Decida um valor exclusivo para o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="1baf0-128">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="1baf0-129">O tipo de declaração é um identificador de cadeia de caracteres exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-129">The claim type is a unique string identifier.</span></span> <span data-ttu-id="1baf0-130">É responsabilidade do designer de declarações personalizado garantir que o identificador de cadeia de caracteres usado para o tipo de declaração seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-130">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="1baf0-131">Para obter uma lista de tipos de declaração que são definidos pelo WCF, consulte a <xref:System.IdentityModel.Claims.ClaimTypes> classe.</span><span class="sxs-lookup"><span data-stu-id="1baf0-131">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="1baf0-132">Escolha ou defina um tipo não primitivo serializável para o recurso.</span><span class="sxs-lookup"><span data-stu-id="1baf0-132">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="1baf0-133">Um recurso é um objeto.</span><span class="sxs-lookup"><span data-stu-id="1baf0-133">A resource is an object.</span></span> <span data-ttu-id="1baf0-134">O tipo CLR do recurso deve ser serializável, pois as declarações são serializadas em vários pontos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="1baf0-134">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="1baf0-135">Tipos primitivos já são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="1baf0-135">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="1baf0-136">Quando um novo tipo é definido, aplique o <xref:System.Runtime.Serialization.DataContractAttribute> à classe.</span><span class="sxs-lookup"><span data-stu-id="1baf0-136">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="1baf0-137">Também aplique o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo a todos os membros do novo tipo que precisa ser serializado como parte da declaração.</span><span class="sxs-lookup"><span data-stu-id="1baf0-137">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="1baf0-138">O exemplo de código a seguir define um tipo de recurso personalizado chamado `MyResourceType` .</span><span class="sxs-lookup"><span data-stu-id="1baf0-138">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="1baf0-139">Escolha um direito que seja definido pelo WCF ou um valor exclusivo para um direito personalizado.</span><span class="sxs-lookup"><span data-stu-id="1baf0-139">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="1baf0-140">A direita é um identificador de cadeia de caracteres exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-140">A right is a unique string identifier.</span></span> <span data-ttu-id="1baf0-141">Os direitos definidos pelo WCF são definidos na <xref:System.IdentityModel.Claims.Rights> classe.</span><span class="sxs-lookup"><span data-stu-id="1baf0-141">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="1baf0-142">É responsabilidade do designer de declarações personalizado garantir que o identificador de cadeia de caracteres usado para a direita seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-142">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="1baf0-143">O exemplo de código a seguir cria uma declaração personalizada com um tipo de declaração de `http://example.org/claims/complexcustomclaim` , um tipo de recurso personalizado de `MyResourceType` e com a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> direita.</span><span class="sxs-lookup"><span data-stu-id="1baf0-143">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="1baf0-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1baf0-144">Example</span></span>  
 <span data-ttu-id="1baf0-145">O exemplo de código a seguir demonstra como criar uma declaração personalizada com um tipo de recurso primitivo e uma declaração personalizada com um tipo de recurso não primitivo.</span><span class="sxs-lookup"><span data-stu-id="1baf0-145">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="1baf0-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="1baf0-146">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="1baf0-147">Gerenciamento de declarações e autorizações com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="1baf0-147">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
