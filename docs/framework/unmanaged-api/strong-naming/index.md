---
title: Nomenclatura forte (referência de API não gerenciada)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce89e27089ea2f0c918d0fe37c4eea141698f9be
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="strong-naming-unmanaged-api-reference"></a>Nomenclatura forte (referência de API não gerenciada)
A API de nomeação forte permite que um cliente administrar a assinatura para assemblies de nome forte.  
  
 Assinar um assembly com um nome forte adiciona uma criptografia de chave pública ao arquivo que contém o manifesto do assembly. Assinatura de nome forte ajuda a verificar exclusividade de nome, impede a falsificação de nome e fornece chamadores com uma identidade exclusiva quando uma referência é resolvida. No entanto, nenhum nível de confiança está associado com um nome forte.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Fortes nomes funções estáticas globais](http://msdn.microsoft.com/library/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 Descreve as funções estáticas globais não gerenciadas que usa a API de nomeação forte.  
  
> [!NOTE]
>  Todas essas funções foram preteridas a partir de [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Para alternativas sugeridas, consulte o [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) interface.  
  
 [Função GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Obtém um hash do arquivo de assembly especificado, usando o algoritmo de hash especificado. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Obtém um hash do arquivo de assembly especificado como uma cadeia de caracteres Unicode, usando o algoritmo de hash especificado. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromBlob](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Gera um hash com base no conteúdo do arquivo especificado.  Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Gera um hash com base no conteúdo do arquivo especificado por uma cadeia de caracteres Unicode. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromHandle](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Gera um hash com base no conteúdo do arquivo com o identificador de arquivo especificado, usando o algoritmo de hash especificado.  Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 Determina se os dois assemblies diferem somente por suas assinaturas de nome forte. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Obtém o último código de erro que foi gerado por uma das funções de nome forte.  
  
 [Função StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameGetBlob](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Obtém uma representação binária da imagem do assembly no endereço de memória especificado. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Obtém a chave pública de um par de chaves pública/privada. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameHashSize](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.  Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Exclui o contêiner de chave especificado. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameKeyGen](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Cria um novo par de chaves pública/privada para uso de nome forte.  Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Gera um novo par de chaves pública/privada com o tamanho da chave especificado para o uso de nome forte. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Importa um par de chaves pública/privada para um contêiner.  Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Gera uma assinatura de nome forte para o assembly especificado.   Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Gera uma assinatura de nome forte para o assembly especificado, com base nos sinalizadores especificados.    Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Retorna o tamanho da assinatura de nome forte. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.  Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureVerificationFromImage](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Verifica se um assembly que já foi mapeado para a memória é válido para a chave pública associada. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Cria um token de nome forte do arquivo de assembly especificado.  Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Cria um token de nome forte do arquivo de assembly especificado e retorna a chave pública. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Obtém um token que representa uma chave pública. Preteridos a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Estrutura de nomenclatura forte](http://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 Descreve a estrutura não gerenciada que usa a API de nomeação forte para administrar a assinatura para assemblies de nome forte.  
  
 [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Representa a chave pública de um par de chaves pública/privada em formato binário.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [Referência de API não gerenciada](../../../../docs/framework/unmanaged-api/index.md)
