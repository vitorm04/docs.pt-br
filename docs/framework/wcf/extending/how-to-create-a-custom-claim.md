---
title: Como criar uma afirmação personalizada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185613"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="9b887-102">Como criar uma afirmação personalizada</span><span class="sxs-lookup"><span data-stu-id="9b887-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="9b887-103">A infra-estrutura do Modelo de Identidade na Windows Communication Foundation (WCF) fornece um <xref:System.IdentityModel.Claims.Claim> conjunto de tipos e direitos de reclamação incorporados com as funções de ajudante para criar instâncias com esses tipos e direitos.</span><span class="sxs-lookup"><span data-stu-id="9b887-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="9b887-104">Essas reivindicações incorporadas são projetadas para modelar informações encontradas em tipos de credenciais de clientes que o WCF suporta por padrão.</span><span class="sxs-lookup"><span data-stu-id="9b887-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="9b887-105">Em muitos casos, as reivindicações incorporadas são suficientes; no entanto, alguns aplicativos podem exigir reivindicações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9b887-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="9b887-106">Uma reclamação consiste no tipo de sinistro, o recurso para o qual a reclamação se aplica e o direito que é afirmado sobre esse recurso.</span><span class="sxs-lookup"><span data-stu-id="9b887-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="9b887-107">Este tópico descreve como criar uma reivindicação personalizada.</span><span class="sxs-lookup"><span data-stu-id="9b887-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="9b887-108">Para criar uma reivindicação personalizada que é baseada em um tipo de dados primitivo</span><span class="sxs-lookup"><span data-stu-id="9b887-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="9b887-109">Crie uma reclamação personalizada passando o tipo de <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> reclamação, o valor do recurso e o direito ao construtor.</span><span class="sxs-lookup"><span data-stu-id="9b887-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="9b887-110">Decida sobre um valor único para o tipo de sinistro.</span><span class="sxs-lookup"><span data-stu-id="9b887-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="9b887-111">O tipo de reclamação é um identificador de string único.</span><span class="sxs-lookup"><span data-stu-id="9b887-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="9b887-112">É responsabilidade do designer de reivindicações personalizado garantir que o identificador de string usado para o tipo de sinistro seja único.</span><span class="sxs-lookup"><span data-stu-id="9b887-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="9b887-113">Para obter uma lista de tipos de sinistro <xref:System.IdentityModel.Claims.ClaimTypes> definidos pelo WCF, consulte a classe.</span><span class="sxs-lookup"><span data-stu-id="9b887-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="9b887-114">Escolha o tipo de dados primitivo e o valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="9b887-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="9b887-115">Um recurso é um objeto.</span><span class="sxs-lookup"><span data-stu-id="9b887-115">A resource is an object.</span></span> <span data-ttu-id="9b887-116">O tipo CLR do recurso pode ser <xref:System.String> <xref:System.Int32>primitivo, como ou , ou qualquer tipo serializável.</span><span class="sxs-lookup"><span data-stu-id="9b887-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="9b887-117">O tipo CLR do recurso deve ser serializável, porque as reivindicações são serializadas em vários pontos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="9b887-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="9b887-118">Tipos primitivos são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="9b887-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="9b887-119">Escolha um direito definido pelo WCF ou um valor único para um direito personalizado.</span><span class="sxs-lookup"><span data-stu-id="9b887-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="9b887-120">A direita é um identificador de string único.</span><span class="sxs-lookup"><span data-stu-id="9b887-120">A right is a unique string identifier.</span></span> <span data-ttu-id="9b887-121">Os direitos definidos pelo WCF <xref:System.IdentityModel.Claims.Rights> são definidos na classe.</span><span class="sxs-lookup"><span data-stu-id="9b887-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="9b887-122">É responsabilidade do designer de reivindicações personalizado garantir que o identificador de string que é usado para a direita seja único.</span><span class="sxs-lookup"><span data-stu-id="9b887-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="9b887-123">O exemplo de código a seguir cria `http://example.org/claims/simplecustomclaim`uma reclamação `Driver's License`personalizada com <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> um tipo de reclamação de , para um recurso chamado , e com o direito.</span><span class="sxs-lookup"><span data-stu-id="9b887-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="9b887-124">Para criar uma reivindicação personalizada baseada em um tipo de dados não primitivo</span><span class="sxs-lookup"><span data-stu-id="9b887-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="9b887-125">Crie uma reclamação personalizada passando o tipo de <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> reclamação, o valor do recurso e o direito ao construtor.</span><span class="sxs-lookup"><span data-stu-id="9b887-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="9b887-126">Decida sobre um valor único para o tipo de sinistro.</span><span class="sxs-lookup"><span data-stu-id="9b887-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="9b887-127">O tipo de reclamação é um identificador de string único.</span><span class="sxs-lookup"><span data-stu-id="9b887-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="9b887-128">É responsabilidade do designer de reivindicações personalizado garantir que o identificador de string usado para o tipo de sinistro seja único.</span><span class="sxs-lookup"><span data-stu-id="9b887-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="9b887-129">Para obter uma lista de tipos de sinistro <xref:System.IdentityModel.Claims.ClaimTypes> definidos pelo WCF, consulte a classe.</span><span class="sxs-lookup"><span data-stu-id="9b887-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="9b887-130">Escolha ou defina um tipo serializável não primitivo para o recurso.</span><span class="sxs-lookup"><span data-stu-id="9b887-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="9b887-131">Um recurso é um objeto.</span><span class="sxs-lookup"><span data-stu-id="9b887-131">A resource is an object.</span></span> <span data-ttu-id="9b887-132">O tipo CLR do recurso deve ser serializável, porque as reivindicações são serializadas em vários pontos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="9b887-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="9b887-133">Tipos primitivos já são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="9b887-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="9b887-134">Quando um novo tipo for <xref:System.Runtime.Serialization.DataContractAttribute> definido, aplique o na classe.</span><span class="sxs-lookup"><span data-stu-id="9b887-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="9b887-135">Também aplique <xref:System.Runtime.Serialization.DataMemberAttribute> o atributo a todos os membros do novo tipo que precisam ser serializados como parte da reivindicação.</span><span class="sxs-lookup"><span data-stu-id="9b887-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="9b887-136">O exemplo de código a seguir `MyResourceType`define um tipo de recurso personalizado chamado .</span><span class="sxs-lookup"><span data-stu-id="9b887-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="9b887-137">Escolha um direito definido pelo WCF ou um valor único para um direito personalizado.</span><span class="sxs-lookup"><span data-stu-id="9b887-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="9b887-138">A direita é um identificador de string único.</span><span class="sxs-lookup"><span data-stu-id="9b887-138">A right is a unique string identifier.</span></span> <span data-ttu-id="9b887-139">Os direitos definidos pelo WCF <xref:System.IdentityModel.Claims.Rights> são definidos na classe.</span><span class="sxs-lookup"><span data-stu-id="9b887-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="9b887-140">É responsabilidade do designer de reivindicações personalizado garantir que o identificador de string que é usado para a direita seja único.</span><span class="sxs-lookup"><span data-stu-id="9b887-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="9b887-141">O exemplo de código a seguir cria `http://example.org/claims/complexcustomclaim`uma reclamação personalizada `MyResourceType`com um <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> tipo de reclamação de , um tipo de recurso personalizado de , e com o direito.</span><span class="sxs-lookup"><span data-stu-id="9b887-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="9b887-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b887-142">Example</span></span>  
 <span data-ttu-id="9b887-143">O exemplo de código a seguir demonstra como criar uma reivindicação personalizada com um tipo de recurso primitivo e uma reivindicação personalizada com um tipo de recurso não primitivo.</span><span class="sxs-lookup"><span data-stu-id="9b887-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="9b887-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b887-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="9b887-145">Gerenciamento de declarações e autorizações com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="9b887-145">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
