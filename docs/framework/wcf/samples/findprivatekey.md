---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81ca357ccdcbe76f36f3ba56caf2013a80143728
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="findprivatekey"></a><span data-ttu-id="ae4e4-102">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="ae4e4-102">FindPrivateKey</span></span>
<span data-ttu-id="ae4e4-103">Pode ser difícil encontrar o local e o nome do arquivo da chave privado associado com um certificado x. 509 específico no repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="ae4e4-104">A ferramenta FindPrivateKey.exe facilita esse processo.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-104">The FindPrivateKey.exe tool facilitates this process.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae4e4-105">FindPrivateKey é um exemplo que devem ser compilados antes do uso.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="ae4e4-106">Consulte a seção "para criar o projeto de FindPrivateKey" abaixo para obter instruções sobre como criar a ferramenta FindPrivateKey.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-106">See the "To build the FindPrivateKey project" section below for instructions on how to build the FindPrivateKey tool.</span></span>  
  
 <span data-ttu-id="ae4e4-107">Certificados x. 509 são instalados por um administrador ou a qualquer usuário na máquina.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="ae4e4-108">No entanto, o certificado pode ser acessado por um serviço executado sob uma conta diferente (por exemplo, o ASPNET em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou as contas de serviço de rede em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="ae4e4-108">However the certificate may be accessed by a service running under a different account (for example, the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE accounts on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span></span>  
  
 <span data-ttu-id="ae4e4-109">Essa conta pode não ter acesso ao arquivo de chave privado porque o certificado não foram instalado originalmente por ele.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-109">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="ae4e4-110">A ferramenta FindPrivateKey fornece o local do arquivo de chave privada do certificado x. 509 determinado.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-110">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="ae4e4-111">Você pode adicionar permissões ou remover permissões para esse arquivo quando você souber o local do arquivo de chave privada dos certificados x. 509 específico.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-111">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>  
  
 <span data-ttu-id="ae4e4-112">Os exemplos que usam certificados para segurança de usam a ferramenta de FindPrivateKey no arquivo bat.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-112">The samples that use certificates for security use the FindPrivateKey tool in the Setup.bat file.</span></span> <span data-ttu-id="ae4e4-113">Depois que o arquivo de chave privada foi encontrado, você pode usar outras ferramentas, como Cacls.exe para definir os direitos de acesso apropriados para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-113">Once the private key file has been found you can use other tools such as Cacls.exe to set the appropriate access rights onto the file.</span></span>  
  
 <span data-ttu-id="ae4e4-114">Ao executar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço sob uma conta de usuário, como um executável auto-hospedado, certifique-se de que a conta de usuário tem acesso somente leitura ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-114">When running a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="ae4e4-115">Ao executar uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço em Internet Information Services (IIS) as contas padrão que o serviço é executado são o ASPNET em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou o serviço de rede em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], que por padrão não tem acesso ao arquivo de chave privado.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-115">When running a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under Internet Information Services (IIS) the default accounts that the service runs under are the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], which by default do not have access to the private key file.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ae4e4-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ae4e4-116">Examples</span></span>  
 <span data-ttu-id="ae4e4-117">Ao acessar um certificado para o qual o processo não tem o privilégio de leitura, verá uma mensagem de exceção semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-117">When accessing a certificate for which the process does not have read privilege, you see an exception message similar to the following example.</span></span>  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 <span data-ttu-id="ae4e4-118">Quando isso ocorre use a ferramenta de FindPrivateKey para localizar o arquivo de chave privada e, em seguida, defina o acesso certo para o processo que o serviço está em execução.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-118">When this occurs use the FindPrivateKey tool to find the private key file and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="ae4e4-119">Por exemplo, isso pode ser feito com a ferramenta Cacls.exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-119">For example, this can be done with the Cacls.exe tool as shown in the following example.</span></span>  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="ae4e4-120">Para compilar o projeto FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="ae4e4-120">To build the FindPrivateKey project</span></span>  
  
1.  <span data-ttu-id="ae4e4-121">Abra [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e navegue até o subdiretório específico do idioma em que o local do diretório onde você instalou o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-121">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="ae4e4-122">Clique duas vezes no ícone do arquivo. sln para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-122">Double-click the .sln file icon to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="ae4e4-123">No **criar** menu, selecione **recompilar solução**.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-123">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="ae4e4-124">Os arquivos de programa do cliente são criados para client\bin e os arquivos de programa de serviço são criados para service\bin.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-124">The client program files are built to client\bin and the service program files are built to service\bin.</span></span>  
  
4.  <span data-ttu-id="ae4e4-125">Compilar a solução gera o arquivo: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-125">Building the solution generates the file: FindPrivateKey.exe.</span></span>  
  
## <a name="conventionscommand-line-entries"></a><span data-ttu-id="ae4e4-126">Convenções — entradas de linha de comando</span><span class="sxs-lookup"><span data-stu-id="ae4e4-126">Conventions—Command-Line Entries</span></span>  
 <span data-ttu-id="ae4e4-127">"[*opção*]" representa um conjunto opcional de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-127">"[*option*]" represents an optional set of parameters.</span></span>  
  
 <span data-ttu-id="ae4e4-128">"{*opção*}" representa um conjunto de parâmetros de obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-128">"{*option*}" represents a mandatory set of parameters.</span></span>  
  
 <span data-ttu-id="ae4e4-129">"*opção 1* &#124; *option2*"representa uma opção entre conjuntos de opções.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-129">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>  
  
 <span data-ttu-id="ae4e4-130">"\<*valor*>" representa um valor de parâmetro a ser inserido.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-130">"\<*value*>" represents a parameter value to be entered.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="ae4e4-131">Uso</span><span class="sxs-lookup"><span data-stu-id="ae4e4-131">Usage</span></span>  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 <span data-ttu-id="ae4e4-132">Sendo que:</span><span class="sxs-lookup"><span data-stu-id="ae4e4-132">Where:</span></span>  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 <span data-ttu-id="ae4e4-133">Se nenhum parâmetro for especificado no prompt de comando, este texto de Ajuda será exibido.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-133">If no parameters are specified at the command prompt then this help text is displayed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ae4e4-134">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ae4e4-134">Examples</span></span>  
 <span data-ttu-id="ae4e4-135">Este exemplo localiza o nome do arquivo do certificado com um nome de assunto de "CN = localhost", no repositório pessoal do atual User.FindPrivateKey e meu CurrentUser - n "CN = localhost".</span><span class="sxs-lookup"><span data-stu-id="ae4e4-135">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.FindPrivateKey My CurrentUser -n "CN=localhost".</span></span>  
  
 <span data-ttu-id="ae4e4-136">Este exemplo localiza o nome do arquivo do certificado com um nome de assunto de "CN = localhost", em que o pessoal armazenar de atual e o caminho completo do diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-136">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current and output the full directory path.</span></span>  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 <span data-ttu-id="ae4e4-137">Este exemplo localiza o nome do arquivo do certificado com impressão digital "03 33 98 63 e7 47 d0 48 71 33 62 64 76 5c 4c 9d 1 de 42 6b d 52", no repositório pessoal do computador Local.</span><span class="sxs-lookup"><span data-stu-id="ae4e4-137">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae4e4-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae4e4-138">See Also</span></span>
