---
title: Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5a8363b0ec059c1ae94b7ab53e5c3064a06541f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="4fe34-102">Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)</span><span class="sxs-lookup"><span data-stu-id="4fe34-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="4fe34-103">A ferramenta Teste de Certificado do Editor de Software cria um SPC (Software Publisher's Certificate) com base em um ou vários certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="4fe34-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="4fe34-104">Cert2spc.exe é apenas para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="4fe34-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="4fe34-105">É possível obter um SPC válido de uma Autoridade de Certificação como, por exemplo, Verisign ou Thawte.</span><span class="sxs-lookup"><span data-stu-id="4fe34-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="4fe34-106">Para obter mais informações sobre a criação de certificados X.509, consulte [Makecert.exe (Ferramenta de Criação de Certificado)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span><span class="sxs-lookup"><span data-stu-id="4fe34-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span></span>  
  
 <span data-ttu-id="4fe34-107">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4fe34-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4fe34-108">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="4fe34-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4fe34-109">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4fe34-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="4fe34-110">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4fe34-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe34-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fe34-111">Syntax</span></span>  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fe34-112">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4fe34-112">Parameters</span></span>  
  
|<span data-ttu-id="4fe34-113">Argumento</span><span class="sxs-lookup"><span data-stu-id="4fe34-113">Argument</span></span>|<span data-ttu-id="4fe34-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe34-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="4fe34-115">O nome de um certificado X.509 a ser incluído no arquivo SPC.</span><span class="sxs-lookup"><span data-stu-id="4fe34-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="4fe34-116">É possível especificar vários nomes separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="4fe34-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="4fe34-117">O nome de uma lista de revogações do certificado a ser incluída no arquivo SPC.</span><span class="sxs-lookup"><span data-stu-id="4fe34-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="4fe34-118">É possível especificar vários nomes separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="4fe34-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="4fe34-119">O nome do objeto PKCS #7 que conterá os certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="4fe34-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="4fe34-120">Opção</span><span class="sxs-lookup"><span data-stu-id="4fe34-120">Option</span></span>|<span data-ttu-id="4fe34-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe34-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4fe34-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="4fe34-122">**/?**</span></span>|<span data-ttu-id="4fe34-123">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="4fe34-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="4fe34-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4fe34-124">Examples</span></span>  
 <span data-ttu-id="4fe34-125">O comando a seguir cria um SPC com base em `myCertificate.cer` e o coloca em `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="4fe34-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="4fe34-126">O comando a seguir cria um SPC com base em `oneCertificate.cer` e `twoCertificate.cer` e o coloca em `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="4fe34-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fe34-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fe34-127">See Also</span></span>  
 [<span data-ttu-id="4fe34-128">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="4fe34-128">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="4fe34-129">Makecert.exe (Ferramenta de Criação de Certificado)</span><span class="sxs-lookup"><span data-stu-id="4fe34-129">Makecert.exe (Certificate Creation Tool)</span></span>](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="4fe34-130">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="4fe34-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
