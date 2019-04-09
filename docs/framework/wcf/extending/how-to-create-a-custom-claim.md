---
title: 'Como: criar uma declaração personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: fa04b883e37cc287e6bd52ce9f206b2b24fe905f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167421"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="32fde-102">Como: criar uma declaração personalizada</span><span class="sxs-lookup"><span data-stu-id="32fde-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="32fde-103">A infraestrutura de modelo de identidade no Windows Communication Foundation (WCF) fornece um conjunto de tipos de declaração interna e direitos com as funções auxiliares para a criação de <xref:System.IdentityModel.Claims.Claim> instâncias com esses tipos e direitos.</span><span class="sxs-lookup"><span data-stu-id="32fde-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="32fde-104">Essas declarações internas são projetadas para informações sobre o modelo encontrado em tipos de credencial de cliente WCF oferece suporte por padrão.</span><span class="sxs-lookup"><span data-stu-id="32fde-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="32fde-105">Em muitos casos, as declarações internas são suficientes; No entanto, alguns aplicativos podem exigir declarações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="32fde-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="32fde-106">Uma declaração consiste o tipo de declaração, o recurso para o qual a declaração aplica-se a e à direita que é declarada por esse recurso.</span><span class="sxs-lookup"><span data-stu-id="32fde-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="32fde-107">Este tópico descreve como criar uma declaração personalizada.</span><span class="sxs-lookup"><span data-stu-id="32fde-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="32fde-108">Para criar uma declaração personalizada que é baseada em um tipo de dados primitivo</span><span class="sxs-lookup"><span data-stu-id="32fde-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1.  <span data-ttu-id="32fde-109">Criar uma declaração personalizada, passando o tipo de declaração, o valor do recurso e o direito do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> construtor.</span><span class="sxs-lookup"><span data-stu-id="32fde-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="32fde-110">Escolha um valor exclusivo para o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="32fde-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="32fde-111">O tipo de declaração é um identificador de cadeia de caracteres exclusiva.</span><span class="sxs-lookup"><span data-stu-id="32fde-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="32fde-112">É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para o tipo de declaração é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="32fde-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="32fde-113">Para obter uma lista dos tipos de declaração que são definidas pelo WCF, consulte o <xref:System.IdentityModel.Claims.ClaimTypes> classe.</span><span class="sxs-lookup"><span data-stu-id="32fde-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="32fde-114">Escolha o tipo de dados primitivo e o valor para o recurso.</span><span class="sxs-lookup"><span data-stu-id="32fde-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="32fde-115">Um recurso é um objeto.</span><span class="sxs-lookup"><span data-stu-id="32fde-115">A resource is an object.</span></span> <span data-ttu-id="32fde-116">O tipo CLR do recurso pode ser um primitivo, tal como <xref:System.String> ou <xref:System.Int32>, ou qualquer tipo serializável.</span><span class="sxs-lookup"><span data-stu-id="32fde-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="32fde-117">O tipo CLR do recurso deve ser serializável, porque as declarações são serializadas em vários pontos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="32fde-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="32fde-118">Tipos primitivos são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="32fde-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="32fde-119">Escolha um direito que é definido pelo WCF ou um valor exclusivo para um direito personalizado.</span><span class="sxs-lookup"><span data-stu-id="32fde-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="32fde-120">Um direito é um identificador de cadeia de caracteres exclusiva.</span><span class="sxs-lookup"><span data-stu-id="32fde-120">A right is a unique string identifier.</span></span> <span data-ttu-id="32fde-121">Os direitos que são definidos pelo WCF são definidos na <xref:System.IdentityModel.Claims.Rights> classe.</span><span class="sxs-lookup"><span data-stu-id="32fde-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="32fde-122">É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para a direita é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="32fde-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="32fde-123">O exemplo de código a seguir cria uma declaração personalizada com um tipo de declaração de `http://example.org/claims/simplecustomclaim`, para um recurso chamado `Driver's License`e com o <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> à direita.</span><span class="sxs-lookup"><span data-stu-id="32fde-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="32fde-124">Para criar uma declaração personalizada que é baseada em um tipo de dados não primitivos</span><span class="sxs-lookup"><span data-stu-id="32fde-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1.  <span data-ttu-id="32fde-125">Criar uma declaração personalizada, passando o tipo de declaração, o valor do recurso e o direito do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> construtor.</span><span class="sxs-lookup"><span data-stu-id="32fde-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="32fde-126">Escolha um valor exclusivo para o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="32fde-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="32fde-127">O tipo de declaração é um identificador de cadeia de caracteres exclusiva.</span><span class="sxs-lookup"><span data-stu-id="32fde-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="32fde-128">É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para o tipo de declaração é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="32fde-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="32fde-129">Para obter uma lista dos tipos de declaração que são definidas pelo WCF, consulte o <xref:System.IdentityModel.Claims.ClaimTypes> classe.</span><span class="sxs-lookup"><span data-stu-id="32fde-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="32fde-130">Escolha ou definir um tipo não primitivo serializável para o recurso.</span><span class="sxs-lookup"><span data-stu-id="32fde-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="32fde-131">Um recurso é um objeto.</span><span class="sxs-lookup"><span data-stu-id="32fde-131">A resource is an object.</span></span> <span data-ttu-id="32fde-132">O tipo CLR do recurso deve ser serializável, porque as declarações são serializadas em vários pontos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="32fde-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="32fde-133">Tipos primitivos já são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="32fde-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="32fde-134">Quando um novo tipo é definido, aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> à classe.</span><span class="sxs-lookup"><span data-stu-id="32fde-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="32fde-135">Também se aplicam a <xref:System.Runtime.Serialization.DataMemberAttribute> a todos os membros do novo tipo de que precisam ser serializados como parte da declaração de atributo.</span><span class="sxs-lookup"><span data-stu-id="32fde-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="32fde-136">O exemplo de código a seguir define um tipo de recurso personalizado chamado `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="32fde-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="32fde-137">Escolha um direito que é definido pelo WCF ou um valor exclusivo para um direito personalizado.</span><span class="sxs-lookup"><span data-stu-id="32fde-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="32fde-138">Um direito é um identificador de cadeia de caracteres exclusiva.</span><span class="sxs-lookup"><span data-stu-id="32fde-138">A right is a unique string identifier.</span></span> <span data-ttu-id="32fde-139">Os direitos que são definidos pelo WCF são definidos na <xref:System.IdentityModel.Claims.Rights> classe.</span><span class="sxs-lookup"><span data-stu-id="32fde-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="32fde-140">É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para a direita é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="32fde-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="32fde-141">O exemplo de código a seguir cria uma declaração personalizada com um tipo de declaração de `http://example.org/claims/complexcustomclaim`, um tipo de recurso personalizado de `MyResourceType`e com o <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> à direita.</span><span class="sxs-lookup"><span data-stu-id="32fde-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="32fde-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="32fde-142">Example</span></span>  
 <span data-ttu-id="32fde-143">O exemplo de código a seguir demonstra como criar uma declaração personalizada com um tipo de recurso primitivos e uma declaração personalizada com um tipo de recurso não primitivo.</span><span class="sxs-lookup"><span data-stu-id="32fde-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="32fde-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32fde-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="32fde-145">Gerenciamento de declarações e autorizações com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="32fde-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
