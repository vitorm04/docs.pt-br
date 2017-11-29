---
title: Encontrar ferramenta de chave privada (FindPrivateKey.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5e2110e129b293ffb04c8e3eb69a5c3bfe83c17b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="eb642-102">Encontrar ferramenta de chave privada (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="eb642-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>
<span data-ttu-id="eb642-103">Essa ferramenta de linha de comando pode ser usada para recuperar uma chave privada de um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="eb642-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="eb642-104">Por exemplo, FindPrivateKey.exe pode ser usado para localizar o local e o nome do arquivo da chave privado associado com um certificado x. 509 específico no repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="eb642-104">For example, FindPrivateKey.exe can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eb642-105">A ferramenta FindPrivateKey é enviada como um exemplo do WCF.</span><span class="sxs-lookup"><span data-stu-id="eb642-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="eb642-106">Para obter mais informações sobre onde encontrar o exemplo e como criá-lo, consulte</span><span class="sxs-lookup"><span data-stu-id="eb642-106">For more information about where to find the sample and how to build it, see</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb642-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb642-107">Syntax</span></span>  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb642-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb642-108">Remarks</span></span>  
 <span data-ttu-id="eb642-109">As tabelas a seguir descrevem os argumentos e as opções que podem ser usadas com a ferramenta de localizar a chave privada (FindPrivateKey.exe).</span><span class="sxs-lookup"><span data-stu-id="eb642-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>  
  
|<span data-ttu-id="eb642-110">Argumento</span><span class="sxs-lookup"><span data-stu-id="eb642-110">Argument</span></span>|<span data-ttu-id="eb642-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb642-111">Description</span></span>|  
|--------------|-----------------|  
|`storeName`|<span data-ttu-id="eb642-112">Nome do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="eb642-112">Name of the certificate store.</span></span>|  
|`storeLocation`|<span data-ttu-id="eb642-113">O local do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="eb642-113">The location of the certificate store.</span></span>|  
  
|<span data-ttu-id="eb642-114">Opção</span><span class="sxs-lookup"><span data-stu-id="eb642-114">Option</span></span>|<span data-ttu-id="eb642-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb642-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="eb642-116">`/n <`*subjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="eb642-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="eb642-117">Especifica o nome da entidade do certificado.</span><span class="sxs-lookup"><span data-stu-id="eb642-117">Specifies the subject name of the certificate.</span></span>|  
|<span data-ttu-id="eb642-118">`/t <`*impressão digital*`>`</span><span class="sxs-lookup"><span data-stu-id="eb642-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="eb642-119">Especifica a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="eb642-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="eb642-120">Use Certmgr.exe para recuperar a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="eb642-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|  
|`/f`|<span data-ttu-id="eb642-121">Gera o nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="eb642-121">Outputs the file name only.</span></span>|  
|`/d`|<span data-ttu-id="eb642-122">Gera o diretório somente.</span><span class="sxs-lookup"><span data-stu-id="eb642-122">Outputs the directory only.</span></span>|  
|`/a`|<span data-ttu-id="eb642-123">Gera o nome de arquivo absoluto.</span><span class="sxs-lookup"><span data-stu-id="eb642-123">Outputs the absolute file name.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="eb642-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="eb642-124">Examples</span></span>  
 <span data-ttu-id="eb642-125">O comando a seguir recupera a chave privada para John Doe.</span><span class="sxs-lookup"><span data-stu-id="eb642-125">The following command retrieves the private key for John Doe.</span></span>  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 <span data-ttu-id="eb642-126">O comando a seguir recupera a chave privada para a máquina local.</span><span class="sxs-lookup"><span data-stu-id="eb642-126">The following command retrieves the private key for the local machine.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
