---
title: Exemplo de FindPrivateKey – WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 4ba4316489c1494da9421bea5c513e44c6eb50a7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989881"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="4edca-102">Exemplo de FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="4edca-102">FindPrivateKey sample</span></span>

<span data-ttu-id="4edca-103">Pode ser difícil encontrar o local e o nome do arquivo de chave privada associado a um certificado X. 509 específico no repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="4edca-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="4edca-104">A ferramenta FindPrivateKey. exe facilita esse processo.</span><span class="sxs-lookup"><span data-stu-id="4edca-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4edca-105">FindPrivateKey é um exemplo que precisa ser compilado antes do uso.</span><span class="sxs-lookup"><span data-stu-id="4edca-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="4edca-106">Consulte a seção [para criar o projeto FindPrivateKey](#to-build-the-findprivatekey-project) para obter instruções sobre como criar a ferramenta FindPrivateKey.</span><span class="sxs-lookup"><span data-stu-id="4edca-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="4edca-107">Os certificados X. 509 são instalados por um administrador ou qualquer usuário no computador.</span><span class="sxs-lookup"><span data-stu-id="4edca-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="4edca-108">No entanto, o certificado pode ser acessado por um serviço em execução em uma conta diferente.</span><span class="sxs-lookup"><span data-stu-id="4edca-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="4edca-109">Por exemplo, a conta de serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="4edca-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="4edca-110">Essa conta pode não ter acesso ao arquivo de chave privada porque o certificado não foi instalado originalmente.</span><span class="sxs-lookup"><span data-stu-id="4edca-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="4edca-111">A ferramenta FindPrivateKey fornece o local de um determinado arquivo de chave privada do certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="4edca-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="4edca-112">Você pode adicionar permissões ou remover permissões para esse arquivo quando souber o local do arquivo de chave privada de certificados X. 509 específico.</span><span class="sxs-lookup"><span data-stu-id="4edca-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="4edca-113">Os exemplos que usam certificados para segurança usam a ferramenta FindPrivateKey no arquivo *Setup. bat* .</span><span class="sxs-lookup"><span data-stu-id="4edca-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="4edca-114">Depois que o arquivo de chave privada for encontrado, você poderá usar outras ferramentas, como *cacls. exe* , para definir os direitos de acesso apropriados no arquivo.</span><span class="sxs-lookup"><span data-stu-id="4edca-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="4edca-115">Ao executar um serviço de Windows Communication Foundation (WCF) em uma conta de usuário, como um executável auto-hospedado, verifique se a conta de usuário tem acesso somente leitura ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="4edca-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="4edca-116">Ao executar um serviço WCF em Serviços de Informações da Internet (IIS), as contas padrão nas quais o serviço é executado são o serviço de rede no IIS 7 e versões anteriores, ou a identidade do pool de aplicativos no IIS 7,5 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="4edca-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="4edca-117">Para obter mais informações, consulte [identidades do pool de aplicativos](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="4edca-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="4edca-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4edca-118">Examples</span></span>

<span data-ttu-id="4edca-119">Ao acessar um certificado para o qual o processo não tem privilégio de leitura, você verá uma mensagem de exceção semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4edca-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="4edca-120">Quando isso ocorrer, use a ferramenta FindPrivateKey para localizar o arquivo de chave privada e, em seguida, defina o direito de acesso para o processo em que o serviço está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="4edca-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="4edca-121">Por exemplo, isso pode ser feito com a ferramenta Cacls. exe, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4edca-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="4edca-122">Para criar o projeto FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="4edca-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="4edca-123">Para baixar o projeto, visite [exemplos de Windows Communication Foundation (WCF) e Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="4edca-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="4edca-124">Abra o explorador de arquivos e navegue até a pasta *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* sob o local do diretório onde você instalou o exemplo.</span><span class="sxs-lookup"><span data-stu-id="4edca-124">Open File Explorer and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="4edca-125">Clique duas vezes no ícone de arquivo. sln para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4edca-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="4edca-126">No menu **Compilar** , selecione **Recompilar solução**.</span><span class="sxs-lookup"><span data-stu-id="4edca-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="4edca-127">A criação da solução gera o arquivo: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="4edca-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="4edca-128">Convenções — entradas de linha de comando</span><span class="sxs-lookup"><span data-stu-id="4edca-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="4edca-129">"[*Option*]" representa um conjunto opcional de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4edca-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="4edca-130">"{*Option*}" representa um conjunto obrigatório de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4edca-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="4edca-131">"*opção 1* &#124; *opção 2*" representa uma opção entre conjuntos de opções.</span><span class="sxs-lookup"><span data-stu-id="4edca-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="4edca-132">"\<*Value*>" representa um valor de parâmetro a ser inserido.</span><span class="sxs-lookup"><span data-stu-id="4edca-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="4edca-133">Uso</span><span class="sxs-lookup"><span data-stu-id="4edca-133">Usage</span></span>

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="4edca-134">Sendo que:</span><span class="sxs-lookup"><span data-stu-id="4edca-134">Where:</span></span>

| <span data-ttu-id="4edca-135">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4edca-135">Parameter</span></span>         | <span data-ttu-id="4edca-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="4edca-136">Description</span></span>                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | <span data-ttu-id="4edca-137">O nome do assunto do certificado</span><span class="sxs-lookup"><span data-stu-id="4edca-137">The subject name of the certificate</span></span>                                               |
| `<thumbprint>`  | <span data-ttu-id="4edca-138">A impressão digital do certificado (você pode usar a ferramenta certmgr. exe para encontrá-lo)</span><span class="sxs-lookup"><span data-stu-id="4edca-138">The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)</span></span> |
| `-f`            | <span data-ttu-id="4edca-139">somente nome do arquivo de saída</span><span class="sxs-lookup"><span data-stu-id="4edca-139">output file name only</span></span>                                                             |
| `-d`            | <span data-ttu-id="4edca-140">somente diretório de saída</span><span class="sxs-lookup"><span data-stu-id="4edca-140">output directory only</span></span>                                                             |
| `-a`            | <span data-ttu-id="4edca-141">nome de arquivo de saída absoluto</span><span class="sxs-lookup"><span data-stu-id="4edca-141">output absolute file name</span></span>                                                         |

<span data-ttu-id="4edca-142">Se nenhum parâmetro for especificado no prompt de comando, o texto de ajuda com essas informações será exibido.</span><span class="sxs-lookup"><span data-stu-id="4edca-142">If no parameters are specified at the command prompt, then help text with this information is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="4edca-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4edca-143">Examples</span></span>

<span data-ttu-id="4edca-144">Este exemplo localiza o nome de arquivo do certificado com um nome de assunto "CN = localhost", no repositório pessoal do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="4edca-144">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="4edca-145">Este exemplo localiza o nome do arquivo do certificado com um nome de assunto "CN = localhost", no repositório pessoal do usuário atual e gera o caminho completo do diretório.</span><span class="sxs-lookup"><span data-stu-id="4edca-145">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="4edca-146">Este exemplo localiza o nome de arquivo do certificado com uma impressão digital de "03 33 98 63 D0 47 E7 48 71 33 62 64 76 5C 4C 9d 42 1D 6B 52", no repositório pessoal do computador local.</span><span class="sxs-lookup"><span data-stu-id="4edca-146">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
