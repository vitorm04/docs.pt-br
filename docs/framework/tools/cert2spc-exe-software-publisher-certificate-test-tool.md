---
title: Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 809b7d0383f172a5fbcb2ac4ac3ffb96ff0b8e20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129882"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="6ed27-102">Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)</span><span class="sxs-lookup"><span data-stu-id="6ed27-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="6ed27-103">A ferramenta Teste de Certificado do Editor de Software cria um SPC (Software Publisher's Certificate) com base em um ou vários certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="6ed27-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="6ed27-104">Cert2spc.exe é apenas para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="6ed27-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="6ed27-105">É possível obter um SPC válido de uma Autoridade de Certificação como, por exemplo, Verisign ou Thawte.</span><span class="sxs-lookup"><span data-stu-id="6ed27-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="6ed27-106">Para obter mais informações sobre a criação de certificados X.509, consulte [Makecert.exe (Ferramenta de Criação de Certificado)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="6ed27-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="6ed27-107">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ed27-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="6ed27-108">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="6ed27-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6ed27-109">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6ed27-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="6ed27-110">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ed27-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed27-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ed27-111">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ed27-112">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ed27-112">Parameters</span></span>  
  
|<span data-ttu-id="6ed27-113">Argumento</span><span class="sxs-lookup"><span data-stu-id="6ed27-113">Argument</span></span>|<span data-ttu-id="6ed27-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ed27-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="6ed27-115">O nome de um certificado X.509 a ser incluído no arquivo SPC.</span><span class="sxs-lookup"><span data-stu-id="6ed27-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="6ed27-116">É possível especificar vários nomes separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="6ed27-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="6ed27-117">O nome de uma lista de revogações do certificado a ser incluída no arquivo SPC.</span><span class="sxs-lookup"><span data-stu-id="6ed27-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="6ed27-118">É possível especificar vários nomes separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="6ed27-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="6ed27-119">O nome do objeto PKCS #7 que conterá os certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="6ed27-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="6ed27-120">Opção</span><span class="sxs-lookup"><span data-stu-id="6ed27-120">Option</span></span>|<span data-ttu-id="6ed27-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ed27-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6ed27-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="6ed27-122">**/?**</span></span>|<span data-ttu-id="6ed27-123">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ed27-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="6ed27-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6ed27-124">Examples</span></span>  
 <span data-ttu-id="6ed27-125">O comando a seguir cria um SPC com base em `myCertificate.cer` e o coloca em `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="6ed27-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="6ed27-126">O comando a seguir cria um SPC com base em `oneCertificate.cer` e `twoCertificate.cer` e o coloca em `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="6ed27-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ed27-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ed27-127">See also</span></span>

- [<span data-ttu-id="6ed27-128">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="6ed27-128">Tools</span></span>](index.md)
- [<span data-ttu-id="6ed27-129">Makecert.exe (Ferramenta de Criação de Certificado)</span><span class="sxs-lookup"><span data-stu-id="6ed27-129">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="6ed27-130">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="6ed27-130">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
