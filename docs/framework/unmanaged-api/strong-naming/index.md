---
title: Nomenclatura forte (referência de API não gerenciada)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140639"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="8ef43-102">Nomenclatura forte (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="8ef43-102">Strong Naming (Unmanaged API Reference)</span></span>
<span data-ttu-id="8ef43-103">A API de nomenclatura forte permite que um cliente administre a assinatura de nome forte para assemblies.</span><span class="sxs-lookup"><span data-stu-id="8ef43-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="8ef43-104">Assinar um assembly com um nome forte adiciona uma criptografia de chave pública ao arquivo que contém o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="8ef43-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="8ef43-105">Assinatura de nome forte ajuda a verificar a exclusividade do nome, a evitar falsificação de nome e a fornecer chamadores com uma identidade exclusiva quando uma referência é resolvida.</span><span class="sxs-lookup"><span data-stu-id="8ef43-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="8ef43-106">No entanto, nenhum nível de confiança está associado a um nome forte.</span><span class="sxs-lookup"><span data-stu-id="8ef43-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ef43-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8ef43-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ef43-108">Todas essas funções foram preteridas a partir do .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8ef43-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="8ef43-109">Para alternativas sugeridas, consulte a interface [ICLRStrongName](../hosting/iclrstrongname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8ef43-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="8ef43-110">Função GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="8ef43-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="8ef43-111">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="8ef43-112">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-113">Função GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="8ef43-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="8ef43-114">Obtém um hash do arquivo do assembly especificado como uma cadeia de caracteres Unicode, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="8ef43-115">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-116">Função GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="8ef43-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="8ef43-117">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="8ef43-118">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-119">Função GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="8ef43-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="8ef43-120">Gera um hash sobre o conteúdo do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="8ef43-121">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-122">Função GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="8ef43-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="8ef43-123">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="8ef43-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="8ef43-124">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-125">Função GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="8ef43-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="8ef43-126">Gera um hash sobre o conteúdo do arquivo com o identificador de arquivo especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="8ef43-127">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-128">Função StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="8ef43-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="8ef43-129">Determina se dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="8ef43-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="8ef43-130">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-131">Função StrongNameErrorInfo</span><span class="sxs-lookup"><span data-stu-id="8ef43-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="8ef43-132">Obtém o último código de erro que foi gerado por uma das funções de nome forte.</span><span class="sxs-lookup"><span data-stu-id="8ef43-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="8ef43-133">Função StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="8ef43-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="8ef43-134">Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="8ef43-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="8ef43-135">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-136">Função StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="8ef43-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="8ef43-137">Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="8ef43-138">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-139">Função StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="8ef43-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="8ef43-140">Obtém uma representação binária da imagem do assembly no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="8ef43-141">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-142">Função StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="8ef43-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="8ef43-143">Obtém a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="8ef43-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="8ef43-144">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-145">Função StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="8ef43-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="8ef43-146">Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="8ef43-147">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-148">Função StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="8ef43-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="8ef43-149">Exclui o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-149">Deletes the specified key container.</span></span> <span data-ttu-id="8ef43-150">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-151">Função StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="8ef43-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="8ef43-152">Cria um novo par de chaves públicas/privadas para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="8ef43-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="8ef43-153">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-154">Função StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="8ef43-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="8ef43-155">Gera um novo par de chaves públicas/privadas com o tamanho da chave especificado para o uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="8ef43-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="8ef43-156">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-157">Função StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="8ef43-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="8ef43-158">Importa um par de chaves públicas/privadas em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="8ef43-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="8ef43-159">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-160">Função StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="8ef43-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="8ef43-161">Gera uma assinatura de nome forte para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="8ef43-162">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-163">Função StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="8ef43-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="8ef43-164">Gera uma assinatura de nome forte para o assembly especificado, com base nos sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="8ef43-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="8ef43-165">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-166">Função StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="8ef43-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="8ef43-167">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="8ef43-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="8ef43-168">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-169">Função StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="8ef43-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="8ef43-170">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="8ef43-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="8ef43-171">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-172">Função StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="8ef43-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="8ef43-173">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="8ef43-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="8ef43-174">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-175">Função StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="8ef43-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="8ef43-176">Verifica se um assembly, que já foi mapeado para a memória, é válido para a chave pública associada.</span><span class="sxs-lookup"><span data-stu-id="8ef43-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="8ef43-177">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-178">Função StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="8ef43-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="8ef43-179">Cria um token de nome forte do arquivo do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="8ef43-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="8ef43-180">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-181">Função StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="8ef43-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="8ef43-182">Cria um token de nome forte por meio do arquivo do assembly especificado e retorna a chave pública.</span><span class="sxs-lookup"><span data-stu-id="8ef43-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="8ef43-183">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-184">Função StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="8ef43-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="8ef43-185">Obtém um token que representa uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="8ef43-185">Gets a token representing a public key.</span></span> <span data-ttu-id="8ef43-186">Preteridos do .NET Framework 4 em diante.</span><span class="sxs-lookup"><span data-stu-id="8ef43-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="8ef43-187">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="8ef43-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="8ef43-188">Representa a chave pública de um par de chaves públicas/privadas em formato binário.</span><span class="sxs-lookup"><span data-stu-id="8ef43-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef43-189">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ef43-189">See also</span></span>

- [<span data-ttu-id="8ef43-190">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="8ef43-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="8ef43-191">Referência de API não gerenciada</span><span class="sxs-lookup"><span data-stu-id="8ef43-191">Unmanaged API Reference</span></span>](../index.md)
