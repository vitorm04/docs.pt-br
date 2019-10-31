---
title: Nomenclatura forte aprimorada
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 1d582513b10de88e4e5b9b9ef8c338599d6980f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141166"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="2d94a-102">Nomenclatura forte aprimorada</span><span class="sxs-lookup"><span data-stu-id="2d94a-102">Enhanced strong naming</span></span>
<span data-ttu-id="2d94a-103">Uma assinatura de nome forte é um mecanismo de identidade no .NET Framework para identificar os assemblies.</span><span class="sxs-lookup"><span data-stu-id="2d94a-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="2d94a-104">É uma assinatura digital de chave pública que normalmente é usada para verificar a integridade dos dados que são passados de um remetente (assinante) para um destinatário (verificador).</span><span class="sxs-lookup"><span data-stu-id="2d94a-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="2d94a-105">Essa assinatura é usada como uma identidade exclusiva para um assembly e garante que as referências ao assembly não sejam ambíguas.</span><span class="sxs-lookup"><span data-stu-id="2d94a-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="2d94a-106">O assembly é assinado como parte do processo de compilação e verificado ao ser carregado.</span><span class="sxs-lookup"><span data-stu-id="2d94a-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="2d94a-107">Assinaturas de nome forte ajudam a impedir que pessoas mal-intencionadas adulterem um assembly e assinem novamente o assembly com a chave do assinante original.</span><span class="sxs-lookup"><span data-stu-id="2d94a-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="2d94a-108">No entanto, as chaves de nome forte não contêm informações confiáveis sobre o publicador, nem contém uma hierarquia de certificados.</span><span class="sxs-lookup"><span data-stu-id="2d94a-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="2d94a-109">Uma assinatura de nome forte não garante a confiabilidade da pessoa que assinou o assembly, nem indica se a pessoa era um proprietário legítimo da chave, indicando apenas que o proprietário da chave assinou o assembly.</span><span class="sxs-lookup"><span data-stu-id="2d94a-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="2d94a-110">Portanto, não recomendamos usar uma assinatura de nome forte como um validador de segurança para confiar em código de terceiros.</span><span class="sxs-lookup"><span data-stu-id="2d94a-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="2d94a-111">O Microsoft Authenticode é a maneira recomendada para autenticar o código.</span><span class="sxs-lookup"><span data-stu-id="2d94a-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="2d94a-112">Limitações de nomes fortes convencionais</span><span class="sxs-lookup"><span data-stu-id="2d94a-112">Limitations of conventional strong names</span></span>  
 <span data-ttu-id="2d94a-113">A tecnologia de nomeação forte usada nas versões anteriores ao .NET Framework 4.5 têm as seguintes limitações:</span><span class="sxs-lookup"><span data-stu-id="2d94a-113">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="2d94a-114">As chaves estão constantemente sendo atacadas e as técnicas e o hardware aprimorados facilitam a inferência de uma chave privada com base em uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="2d94a-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="2d94a-115">Para se proteger contra ataques, chaves maiores são necessárias.</span><span class="sxs-lookup"><span data-stu-id="2d94a-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="2d94a-116">Versões do .NET framework anteriores ao .NET Framework 4.5 fornecem a capacidade de assinar com chaves de qualquer tamanho (o tamanho padrão é 1.024 bits), mas assinar um assembly com uma nova chave interrompe todos os binários que fazem referência à identidade mais antiga do assembly.</span><span class="sxs-lookup"><span data-stu-id="2d94a-116">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="2d94a-117">Portanto, é extremamente difícil atualizar o tamanho de uma chave de assinatura se você desejar manter a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="2d94a-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="2d94a-118">A assinatura de nome forte dá suporte apenas ao algoritmo SHA-1.</span><span class="sxs-lookup"><span data-stu-id="2d94a-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="2d94a-119">Recentemente, foi descoberto que o SHA-1 é inadequado para aplicativos de hash seguros.</span><span class="sxs-lookup"><span data-stu-id="2d94a-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="2d94a-120">Portanto, um algoritmo mais forte (SHA-256 ou superior) é necessário.</span><span class="sxs-lookup"><span data-stu-id="2d94a-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="2d94a-121">É possível que o SHA-1 perca sua posição de conformidade com o FIPS, o que causaria problemas para aqueles que optarem por usar somente os algoritmos e software em conformidade com FIPS.</span><span class="sxs-lookup"><span data-stu-id="2d94a-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="2d94a-122">Vantagens de nomes fortes aprimorados</span><span class="sxs-lookup"><span data-stu-id="2d94a-122">Advantages of enhanced strong names</span></span>  
 <span data-ttu-id="2d94a-123">As principais vantagens de nomes fortes aprimorados são compatibilidade com nomes fortes já existentes e a capacidade de declarar que uma identidade é equivalente a outra:</span><span class="sxs-lookup"><span data-stu-id="2d94a-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="2d94a-124">Os desenvolvedores que têm assemblies assinados pré-existentes podem migrar suas identidades para os algoritmos SHA-2 enquanto mantém a compatibilidade com os assemblies que referenciam as identidades antigas.</span><span class="sxs-lookup"><span data-stu-id="2d94a-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="2d94a-125">Desenvolvedores que criam novos assemblies e não se preocupam com assinaturas de nome forte pre-existente podem usar os algoritmos SHA-2 mais seguros e assinar os assemblies como de costume.</span><span class="sxs-lookup"><span data-stu-id="2d94a-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="2d94a-126">Usar nomes fortes aprimorados</span><span class="sxs-lookup"><span data-stu-id="2d94a-126">Use enhanced strong names</span></span>  
 <span data-ttu-id="2d94a-127">Chaves de nome forte consistem em uma chave de assinatura e uma chave de identidade.</span><span class="sxs-lookup"><span data-stu-id="2d94a-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="2d94a-128">O assembly é assinado com a chave de assinatura e é identificado pela chave de identidade.</span><span class="sxs-lookup"><span data-stu-id="2d94a-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="2d94a-129">Antes do .NET Framework 4.5, essas duas chaves eram idênticas.</span><span class="sxs-lookup"><span data-stu-id="2d94a-129">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="2d94a-130">Do .NET Framework 4.5 em diante, a chave de identidade permanece a mesma que nas versões anteriores do .NET Framework, mas a chave de assinatura foi aprimorada com um algoritmo de hash mais forte.</span><span class="sxs-lookup"><span data-stu-id="2d94a-130">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="2d94a-131">Além disso, a chave de assinatura é assinada com a chave de identidade para criar uma referenda.</span><span class="sxs-lookup"><span data-stu-id="2d94a-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="2d94a-132">O atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> permite que os metadados de assembly usem a chave pública pré-existente para a identidade do assembly, permitindo que referências ao assembly antigo continuem a funcionar.</span><span class="sxs-lookup"><span data-stu-id="2d94a-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="2d94a-133">O atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> usa a referenda para garantir que o proprietário da nova chave de assinatura também seja o proprietário da chave de identidade antiga.</span><span class="sxs-lookup"><span data-stu-id="2d94a-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="2d94a-134">Assinar com SHA-2, sem a migração de chave</span><span class="sxs-lookup"><span data-stu-id="2d94a-134">Sign with SHA-2, without key migration</span></span>  
 <span data-ttu-id="2d94a-135">Execute os seguintes comandos em um prompt de comando para assinar um assembly sem migrar uma assinatura de nome forte:</span><span class="sxs-lookup"><span data-stu-id="2d94a-135">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="2d94a-136">Gere a nova chave de identidade (se necessário).</span><span class="sxs-lookup"><span data-stu-id="2d94a-136">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="2d94a-137">Extraia a chave pública de identidade e especifique que um algoritmo SHA-2 deve ser usado ao assinar com essa chave.</span><span class="sxs-lookup"><span data-stu-id="2d94a-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="2d94a-138">Assine com atraso o assembly com o arquivo de chave pública de identidade.</span><span class="sxs-lookup"><span data-stu-id="2d94a-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="2d94a-139">Assine novamente o assembly com o par de chaves de identidade completa.</span><span class="sxs-lookup"><span data-stu-id="2d94a-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="2d94a-140">Assinar com SHA-2, com a migração de chave</span><span class="sxs-lookup"><span data-stu-id="2d94a-140">Sign with SHA-2, with key migration</span></span>  
 <span data-ttu-id="2d94a-141">Execute os comandos a seguir em um prompt de comando para assinar um assembly com uma assinatura de nome forte migrada.</span><span class="sxs-lookup"><span data-stu-id="2d94a-141">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="2d94a-142">Gere um par de chaves de identidade e de assinatura (se necessário).</span><span class="sxs-lookup"><span data-stu-id="2d94a-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="2d94a-143">Extraia a chave pública de assinatura e especifique que um algoritmo SHA-2 deve ser usado ao assinar com essa chave.</span><span class="sxs-lookup"><span data-stu-id="2d94a-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="2d94a-144">Extraia a chave pública de identidade, que determina o algoritmo de hash que gera uma referenda.</span><span class="sxs-lookup"><span data-stu-id="2d94a-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="2d94a-145">Gere os parâmetros para um atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> e, em seguida, anexe o atributo ao assembly.</span><span class="sxs-lookup"><span data-stu-id="2d94a-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="2d94a-146">Isso produz uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="2d94a-146">This produces output similar to the following.</span></span>

    ```output
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    <span data-ttu-id="2d94a-147">Essa saída pode, então, ser transformada em um AssemblySignatureKeyAttribute.</span><span class="sxs-lookup"><span data-stu-id="2d94a-147">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="2d94a-148">Assine com atraso o assembly com a chave pública de identidade.</span><span class="sxs-lookup"><span data-stu-id="2d94a-148">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="2d94a-149">Assine completamente o assembly com o par de chaves de assinatura.</span><span class="sxs-lookup"><span data-stu-id="2d94a-149">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d94a-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d94a-150">See also</span></span>

- [<span data-ttu-id="2d94a-151">Criar e usar assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="2d94a-151">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
