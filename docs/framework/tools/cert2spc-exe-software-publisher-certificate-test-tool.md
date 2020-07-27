---
title: Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)
description: Use Cert2spc.exe, a ferramenta de teste de certificado do fornecedor de software. Essa ferramenta cria um certificado do fornecedor de software (SPC) de um ou mais certificados X. 509.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 2eb6339aa6f5d23a5b87986410cbeaac2dac2bec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167318"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="f5751-104">Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)</span><span class="sxs-lookup"><span data-stu-id="f5751-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="f5751-105">A ferramenta Teste de Certificado do Editor de Software cria um SPC (Software Publisher's Certificate) com base em um ou vários certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="f5751-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="f5751-106">Cert2spc.exe é apenas para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="f5751-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="f5751-107">É possível obter um SPC válido de uma Autoridade de Certificação como, por exemplo, Verisign ou Thawte.</span><span class="sxs-lookup"><span data-stu-id="f5751-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="f5751-108">Para obter mais informações sobre a criação de certificados X.509, consulte [Makecert.exe (Ferramenta de Criação de Certificado)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="f5751-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="f5751-109">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5751-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="f5751-110">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="f5751-110">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="f5751-111">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f5751-111">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="f5751-112">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f5751-112">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5751-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5751-113">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5751-114">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5751-114">Parameters</span></span>  
  
|<span data-ttu-id="f5751-115">Argumento</span><span class="sxs-lookup"><span data-stu-id="f5751-115">Argument</span></span>|<span data-ttu-id="f5751-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5751-116">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="f5751-117">O nome de um certificado X.509 a ser incluído no arquivo SPC.</span><span class="sxs-lookup"><span data-stu-id="f5751-117">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="f5751-118">É possível especificar vários nomes separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="f5751-118">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="f5751-119">O nome de uma lista de revogações do certificado a ser incluída no arquivo SPC.</span><span class="sxs-lookup"><span data-stu-id="f5751-119">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="f5751-120">É possível especificar vários nomes separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="f5751-120">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="f5751-121">O nome do objeto PKCS #7 que conterá os certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="f5751-121">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="f5751-122">Opção</span><span class="sxs-lookup"><span data-stu-id="f5751-122">Option</span></span>|<span data-ttu-id="f5751-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5751-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f5751-124">**/?**</span><span class="sxs-lookup"><span data-stu-id="f5751-124">**/?**</span></span>|<span data-ttu-id="f5751-125">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f5751-125">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="f5751-126">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f5751-126">Examples</span></span>  
 <span data-ttu-id="f5751-127">O comando a seguir cria um SPC com base em `myCertificate.cer` e o coloca em `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="f5751-127">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="f5751-128">O comando a seguir cria um SPC com base em `oneCertificate.cer` e `twoCertificate.cer` e o coloca em `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="f5751-128">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5751-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5751-129">See also</span></span>

- [<span data-ttu-id="f5751-130">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="f5751-130">Tools</span></span>](index.md)
- [<span data-ttu-id="f5751-131">Makecert.exe (Ferramenta de Criação de Certificado)</span><span class="sxs-lookup"><span data-stu-id="f5751-131">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="f5751-132">Prompts de comando</span><span class="sxs-lookup"><span data-stu-id="f5751-132">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
