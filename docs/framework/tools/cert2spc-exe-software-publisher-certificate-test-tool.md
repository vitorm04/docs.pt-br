---
title: Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: 21
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7109f96b6997670afa6ef7c362b9e1a142014fbe
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="d9d95-102">Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)</span><span class="sxs-lookup"><span data-stu-id="d9d95-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="d9d95-103">A ferramenta Teste de Certificado do Editor de Software cria um SPC (Software Publisher's Certificate) com base em um ou vários certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="d9d95-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="d9d95-104">Cert2spc.exe é apenas para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="d9d95-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="d9d95-105">É possível obter um SPC válido de uma Autoridade de Certificação como, por exemplo, Verisign ou Thawte.</span><span class="sxs-lookup"><span data-stu-id="d9d95-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="d9d95-106">Para obter mais informações sobre a criação de certificados X.509, consulte [Makecert.exe (Ferramenta de Criação de Certificado)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span><span class="sxs-lookup"><span data-stu-id="d9d95-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span></span>  
  
 <span data-ttu-id="d9d95-107">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9d95-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="d9d95-108">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="d9d95-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="d9d95-109">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d9d95-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="d9d95-110">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9d95-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d95-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9d95-111">Syntax</span></span>  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9d95-112">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9d95-112">Parameters</span></span>  
  
|<span data-ttu-id="d9d95-113">Argumento</span><span class="sxs-lookup"><span data-stu-id="d9d95-113">Argument</span></span>|<span data-ttu-id="d9d95-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9d95-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="d9d95-115">O nome de um certificado X.509 a ser incluído no arquivo SPC.</span><span class="sxs-lookup"><span data-stu-id="d9d95-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="d9d95-116">É possível especificar vários nomes separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="d9d95-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="d9d95-117">O nome de uma lista de revogações do certificado a ser incluída no arquivo SPC.</span><span class="sxs-lookup"><span data-stu-id="d9d95-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="d9d95-118">É possível especificar vários nomes separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="d9d95-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="d9d95-119">O nome do objeto PKCS #7 que conterá os certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="d9d95-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="d9d95-120">Opção</span><span class="sxs-lookup"><span data-stu-id="d9d95-120">Option</span></span>|<span data-ttu-id="d9d95-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9d95-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d9d95-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="d9d95-122">**/?**</span></span>|<span data-ttu-id="d9d95-123">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d9d95-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="d9d95-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d9d95-124">Examples</span></span>  
 <span data-ttu-id="d9d95-125">O comando a seguir cria um SPC com base em `myCertificate.cer` e o coloca em `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="d9d95-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="d9d95-126">O comando a seguir cria um SPC com base em `oneCertificate.cer` e `twoCertificate.cer` e o coloca em `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="d9d95-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9d95-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9d95-127">See Also</span></span>  
 <span data-ttu-id="d9d95-128">[Ferramentas](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="d9d95-128">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 <span data-ttu-id="d9d95-129">[Makecert.exe (Ferramenta de Criação de Certificado)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) </span><span class="sxs-lookup"><span data-stu-id="d9d95-129">[Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) </span></span>  
 [<span data-ttu-id="d9d95-130">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="d9d95-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

