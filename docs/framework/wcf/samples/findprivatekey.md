---
title: Exemplo de FindPrivateKey - WCF
ms.date: 12/04/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32e1a4a3de01371d67be8d19613b1f29c1ce3c29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="c60a6-102">Exemplo de FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="c60a6-102">FindPrivateKey sample</span></span>

<span data-ttu-id="c60a6-103">Pode ser difícil encontrar o local e o nome do arquivo da chave privado associado com um certificado x. 509 específico no repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="c60a6-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="c60a6-104">A ferramenta FindPrivateKey.exe facilita esse processo.</span><span class="sxs-lookup"><span data-stu-id="c60a6-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c60a6-105">FindPrivateKey é um exemplo que devem ser compilados antes do uso.</span><span class="sxs-lookup"><span data-stu-id="c60a6-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="c60a6-106">Consulte o [para compilar o projeto FindPrivateKey](#to-build-the-findprivatekey-project) seção para obter instruções sobre como criar a ferramenta FindPrivateKey.</span><span class="sxs-lookup"><span data-stu-id="c60a6-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="c60a6-107">Certificados x. 509 são instalados por um administrador ou a qualquer usuário na máquina.</span><span class="sxs-lookup"><span data-stu-id="c60a6-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="c60a6-108">No entanto, o certificado pode ser acessado por um serviço executado sob uma conta diferente.</span><span class="sxs-lookup"><span data-stu-id="c60a6-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="c60a6-109">Por exemplo, a conta de serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="c60a6-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="c60a6-110">Essa conta pode não ter acesso ao arquivo de chave privado porque o certificado não foram instalado originalmente por ele.</span><span class="sxs-lookup"><span data-stu-id="c60a6-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="c60a6-111">A ferramenta FindPrivateKey fornece o local do arquivo de chave privada do certificado x. 509 determinado.</span><span class="sxs-lookup"><span data-stu-id="c60a6-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="c60a6-112">Você pode adicionar permissões ou remover permissões para esse arquivo quando você souber o local do arquivo de chave privada dos certificados x. 509 específico.</span><span class="sxs-lookup"><span data-stu-id="c60a6-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="c60a6-113">Os exemplos que usam certificados para segurança de usam a ferramenta de FindPrivateKey no *bat* arquivo.</span><span class="sxs-lookup"><span data-stu-id="c60a6-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="c60a6-114">Depois que o arquivo de chave privada for encontrado, você pode usar outras ferramentas, como *Cacls.exe* para definir os direitos de acesso apropriados para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c60a6-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="c60a6-115">Quando a execução de um serviço do Windows Communication Foundation (WCF) em uma conta de usuário, como um executável auto-hospedado, certifique-se de que a conta de usuário tem acesso somente leitura ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="c60a6-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="c60a6-116">Ao executar um serviço WCF em serviços de informações da Internet (IIS) as contas padrão que o serviço é executado são o serviço de rede no IIS 7 e versões anteriores, ou a identidade do Pool de aplicativos no IIS 7.5 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="c60a6-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="c60a6-117">Para obter mais informações, consulte [identidades do Pool de aplicativos](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="c60a6-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="c60a6-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c60a6-118">Examples</span></span>

<span data-ttu-id="c60a6-119">Ao acessar um certificado para o qual o processo não tem o privilégio de leitura, verá uma mensagem de exceção semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c60a6-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="c60a6-120">Quando isso ocorrer, use a ferramenta de FindPrivateKey para localizar o arquivo de chave privada e, em seguida, defina o acesso à direita para o processo que o serviço está em execução em.</span><span class="sxs-lookup"><span data-stu-id="c60a6-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="c60a6-121">Por exemplo, isso pode ser feito com a ferramenta Cacls.exe, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c60a6-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="c60a6-122">Para compilar o projeto FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="c60a6-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="c60a6-123">Para baixar o projeto, visite [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="c60a6-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="c60a6-124">Abra [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e navegue até o *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* pasta sob o local do diretório onde você instalou o exemplo.</span><span class="sxs-lookup"><span data-stu-id="c60a6-124">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="c60a6-125">Clique duas vezes no ícone do arquivo. sln para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c60a6-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="c60a6-126">No **criar** menu, selecione **recompilar solução**.</span><span class="sxs-lookup"><span data-stu-id="c60a6-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="c60a6-127">Compilar a solução gera o arquivo: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="c60a6-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="c60a6-128">Convenções — entradas de linha de comando</span><span class="sxs-lookup"><span data-stu-id="c60a6-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="c60a6-129">"[*opção*]" representa um conjunto opcional de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c60a6-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="c60a6-130">"{*opção*}" representa um conjunto de parâmetros de obrigatório.</span><span class="sxs-lookup"><span data-stu-id="c60a6-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="c60a6-131">"*opção 1* &#124; *option2*"representa uma opção entre conjuntos de opções.</span><span class="sxs-lookup"><span data-stu-id="c60a6-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="c60a6-132">"\<*valor*>" representa um valor de parâmetro a ser inserido.</span><span class="sxs-lookup"><span data-stu-id="c60a6-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="c60a6-133">Uso</span><span class="sxs-lookup"><span data-stu-id="c60a6-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="c60a6-134">Sendo que:</span><span class="sxs-lookup"><span data-stu-id="c60a6-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="c60a6-135">Se nenhum parâmetro for especificado no prompt de comando, este texto de Ajuda é exibido.</span><span class="sxs-lookup"><span data-stu-id="c60a6-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="c60a6-136">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c60a6-136">Examples</span></span>

<span data-ttu-id="c60a6-137">Este exemplo localiza o nome do arquivo do certificado com um nome de assunto de "CN = localhost", no repositório pessoal do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="c60a6-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="c60a6-138">Este exemplo localiza o nome do arquivo do certificado com um nome de assunto de "CN = localhost", em que o pessoal armazenar do usuário atual e o caminho completo do diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="c60a6-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="c60a6-139">Este exemplo localiza o nome do arquivo do certificado com impressão digital "03 33 98 63 e7 47 d0 48 71 33 62 64 76 5c 4c 9d 1 de 42 6b d 52", no repositório pessoal do computador Local.</span><span class="sxs-lookup"><span data-stu-id="c60a6-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
