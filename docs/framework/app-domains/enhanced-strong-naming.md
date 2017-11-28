---
title: "Nomeação forte aprimorada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 429a54340cef6d608692abd71311c012afe9a3d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="d9419-102">Nomeação forte aprimorada</span><span class="sxs-lookup"><span data-stu-id="d9419-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="d9419-103">Uma assinatura de nome forte é um mecanismo de identidade no .NET Framework para identificar os assemblies.</span><span class="sxs-lookup"><span data-stu-id="d9419-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="d9419-104">É uma assinatura digital de chave pública que normalmente é usada para verificar a integridade dos dados que são passados de um remetente (assinante) para um destinatário (verificador).</span><span class="sxs-lookup"><span data-stu-id="d9419-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="d9419-105">Essa assinatura é usada como uma identidade exclusiva para um assembly e garante que as referências ao assembly não sejam ambíguas.</span><span class="sxs-lookup"><span data-stu-id="d9419-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="d9419-106">O assembly é assinado como parte do processo de compilação e verificado ao ser carregado.</span><span class="sxs-lookup"><span data-stu-id="d9419-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="d9419-107">Assinaturas de nome forte ajudam a impedir que pessoas mal-intencionadas adulterem um assembly e assinem novamente o assembly com a chave do assinante original.</span><span class="sxs-lookup"><span data-stu-id="d9419-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="d9419-108">No entanto, as chaves de nome forte não contêm informações confiáveis sobre o publicador, nem contém uma hierarquia de certificados.</span><span class="sxs-lookup"><span data-stu-id="d9419-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="d9419-109">Uma assinatura de nome forte não garante a confiabilidade da pessoa que assinou o assembly, nem indica se a pessoa era um proprietário legítimo da chave, indicando apenas que o proprietário da chave assinou o assembly.</span><span class="sxs-lookup"><span data-stu-id="d9419-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="d9419-110">Portanto, não recomendamos usar uma assinatura de nome forte como um validador de segurança para confiar em código de terceiros.</span><span class="sxs-lookup"><span data-stu-id="d9419-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="d9419-111">O Microsoft Authenticode é a maneira recomendada para autenticar o código.</span><span class="sxs-lookup"><span data-stu-id="d9419-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="d9419-112">Limitações de nomes fortes convencionais</span><span class="sxs-lookup"><span data-stu-id="d9419-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="d9419-113">A tecnologia de nomeação forte usada nas versões anteriores ao [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] têm as seguintes limitações:</span><span class="sxs-lookup"><span data-stu-id="d9419-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="d9419-114">As chaves estão constantemente sendo atacadas e as técnicas e o hardware aprimorados facilitam a inferência de uma chave privada com base em uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="d9419-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="d9419-115">Para se proteger contra ataques, chaves maiores são necessárias.</span><span class="sxs-lookup"><span data-stu-id="d9419-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="d9419-116">Versões do .NET framework anteriores ao [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] fornecem a capacidade de assinar com chaves de qualquer tamanho (o tamanho padrão é 1024 bits), mas assinar um assembly com uma nova chave interrompe todos os binários que fazem referência à identidade mais antiga do assembly.</span><span class="sxs-lookup"><span data-stu-id="d9419-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="d9419-117">Portanto, é extremamente difícil atualizar o tamanho de uma chave de assinatura se você desejar manter a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="d9419-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="d9419-118">A assinatura de nome forte dá suporte apenas ao algoritmo SHA-1.</span><span class="sxs-lookup"><span data-stu-id="d9419-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="d9419-119">Recentemente, foi descoberto que o SHA-1 é inadequado para aplicativos de hash seguros.</span><span class="sxs-lookup"><span data-stu-id="d9419-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="d9419-120">Portanto, um algoritmo mais forte (SHA-256 ou superior) é necessário.</span><span class="sxs-lookup"><span data-stu-id="d9419-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="d9419-121">É possível que o SHA-1 perca sua posição de conformidade com o FIPS, o que causaria problemas para aqueles que optarem por usar somente os algoritmos e software em conformidade com FIPS.</span><span class="sxs-lookup"><span data-stu-id="d9419-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="d9419-122">Vantagens de nomes fortes aprimorados</span><span class="sxs-lookup"><span data-stu-id="d9419-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="d9419-123">As principais vantagens de nomes fortes aprimorados são compatibilidade com nomes fortes já existentes e a capacidade de declarar que uma identidade é equivalente a outra:</span><span class="sxs-lookup"><span data-stu-id="d9419-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="d9419-124">Os desenvolvedores que têm assemblies assinados pré-existentes podem migrar suas identidades para os algoritmos SHA-2 enquanto mantém a compatibilidade com os assemblies que referenciam as identidades antigas.</span><span class="sxs-lookup"><span data-stu-id="d9419-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="d9419-125">Desenvolvedores que criam novos assemblies e não se preocupam com assinaturas de nome forte pre-existente podem usar os algoritmos SHA-2 mais seguros e assinar os assemblies como de costume.</span><span class="sxs-lookup"><span data-stu-id="d9419-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="d9419-126">Usando nomes fortes aprimorados</span><span class="sxs-lookup"><span data-stu-id="d9419-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="d9419-127">Chaves de nome forte consistem em uma chave de assinatura e uma chave de identidade.</span><span class="sxs-lookup"><span data-stu-id="d9419-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="d9419-128">O assembly é assinado com a chave de assinatura e é identificado pela chave de identidade.</span><span class="sxs-lookup"><span data-stu-id="d9419-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="d9419-129">Antes do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], essas duas chaves eram idênticas.</span><span class="sxs-lookup"><span data-stu-id="d9419-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="d9419-130">A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], a chave de identidade permanece a mesma que nas versões anteriores do .NET Framework, mas a chave de assinatura foi aprimorada com um algoritmo de hash mais forte.</span><span class="sxs-lookup"><span data-stu-id="d9419-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="d9419-131">Além disso, a chave de assinatura é assinada com a chave de identidade para criar uma referenda.</span><span class="sxs-lookup"><span data-stu-id="d9419-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="d9419-132">O atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> permite que os metadados de assembly usem a chave pública pré-existente para a identidade do assembly, permitindo que referências ao assembly antigo continuem a funcionar.</span><span class="sxs-lookup"><span data-stu-id="d9419-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="d9419-133">O atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> usa a referenda para garantir que o proprietário da nova chave de assinatura também seja o proprietário da chave de identidade antiga.</span><span class="sxs-lookup"><span data-stu-id="d9419-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="d9419-134">Assinar com SHA-2 sem migração de chave</span><span class="sxs-lookup"><span data-stu-id="d9419-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="d9419-135">Execute os seguintes comandos em uma janela do Prompt de comando para assinar um assembly sem migrar uma assinatura de nome forte:</span><span class="sxs-lookup"><span data-stu-id="d9419-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="d9419-136">Gere a nova chave de identidade (se necessário).</span><span class="sxs-lookup"><span data-stu-id="d9419-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="d9419-137">Extraia a chave pública de identidade e especifique que um algoritmo SHA-2 deve ser usado ao assinar com essa chave.</span><span class="sxs-lookup"><span data-stu-id="d9419-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="d9419-138">Assine com atraso o assembly com o arquivo de chave pública de identidade.</span><span class="sxs-lookup"><span data-stu-id="d9419-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="d9419-139">Assine novamente o assembly com o par de chaves de identidade completa.</span><span class="sxs-lookup"><span data-stu-id="d9419-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="d9419-140">Assinar com SHA-2 com migração de chave</span><span class="sxs-lookup"><span data-stu-id="d9419-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="d9419-141">Execute os seguintes comandos em uma janela de Prompt de comando para assinar um assembly com uma assinatura de nome forte migrado.</span><span class="sxs-lookup"><span data-stu-id="d9419-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="d9419-142">Gere um par de chaves de identidade e de assinatura (se necessário).</span><span class="sxs-lookup"><span data-stu-id="d9419-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="d9419-143">Extraia a chave pública de assinatura e especifique que um algoritmo SHA-2 deve ser usado ao assinar com essa chave.</span><span class="sxs-lookup"><span data-stu-id="d9419-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="d9419-144">Extraia a chave pública de identidade, que determina o algoritmo de hash que gera uma referenda.</span><span class="sxs-lookup"><span data-stu-id="d9419-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="d9419-145">Gere os parâmetros para um atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> e, em seguida, anexe o atributo ao assembly.</span><span class="sxs-lookup"><span data-stu-id="d9419-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  <span data-ttu-id="d9419-146">Assine com atraso o assembly com a chave pública de identidade.</span><span class="sxs-lookup"><span data-stu-id="d9419-146">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="d9419-147">Assine completamente o assembly com o par de chaves de assinatura.</span><span class="sxs-lookup"><span data-stu-id="d9419-147">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d9419-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9419-148">See Also</span></span>  
 [<span data-ttu-id="d9419-149">Criar e usar assemblies de nomes fortes</span><span class="sxs-lookup"><span data-stu-id="d9419-149">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
