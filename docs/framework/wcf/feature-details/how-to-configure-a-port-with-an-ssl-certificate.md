---
title: Como configurar uma porta com um certificado SSL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 30b24c4ff06cc7249d3ddb6d95549a574e313f52
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579612"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="62544-102">Como configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="62544-102">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="62544-103">Ao criar um serviço de Windows Communication Foundation (WCF) auto-hospedado com a <xref:System.ServiceModel.WSHttpBinding> classe que usa a segurança de transporte, você também deve configurar uma porta com um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="62544-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="62544-104">Se você estiver criando um serviço auto-hospedado, você poderá hospedá-lo serviço no IIS (Serviços de Informações da Internet).</span><span class="sxs-lookup"><span data-stu-id="62544-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="62544-105">Para obter mais informações, consulte [segurança de transporte http](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="62544-105">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="62544-106">Para configurar uma porta, a ferramenta usada depende do sistema operacional que está sendo executado no computador.</span><span class="sxs-lookup"><span data-stu-id="62544-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="62544-107">Se você estiver executando o Windows Server 2003, use a ferramenta HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="62544-107">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="62544-108">No Windows Server 2003, essa ferramenta está instalada.</span><span class="sxs-lookup"><span data-stu-id="62544-108">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="62544-109">Para obter mais informações, consulte a [visão geral do Httpcfg](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="62544-109">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="62544-110">A [documentação das ferramentas de suporte do Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explica a sintaxe da ferramenta Httpcfg. exe.</span><span class="sxs-lookup"><span data-stu-id="62544-110">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="62544-111">Se você estiver executando o Windows Vista, use a ferramenta Netsh. exe que já está instalada.</span><span class="sxs-lookup"><span data-stu-id="62544-111">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="62544-112">A modificação de certificados armazenados no computador requer privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="62544-112">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="62544-113">Determinar como as portas são configuradas</span><span class="sxs-lookup"><span data-stu-id="62544-113">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="62544-114">No Windows Server 2003 ou no Windows XP, use a ferramenta HttpCfg. exe para exibir a configuração da porta atual, usando os comutadores **SSL** e de **consulta** , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="62544-114">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="62544-115">No Windows Vista, use a ferramenta Netsh. exe para exibir a configuração da porta atual, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="62544-115">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="62544-116">Obter a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="62544-116">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="62544-117">Use o snap-in do MMC dos Certificados para localizar um certificado X.509 cuja finalidade seja a autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="62544-117">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="62544-118">Para saber mais, consulte [Como Exibir Certificados com o Snap-in do MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="62544-118">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="62544-119">Para acessar a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="62544-119">Access the certificate's thumbprint.</span></span> <span data-ttu-id="62544-120">Para saber mais, confira [Como recuperar a impressão digital de um certificado](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="62544-120">For more information, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="62544-121">Copie a impressão digital do certificado em um editor de texto, como o Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="62544-121">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="62544-122">Remova todos os espaços entre os caracteres hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="62544-122">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="62544-123">Uma maneira de fazer isso é usar o recurso localizar e substituir do editor de texto e substituir cada espaço com um caractere nulo.</span><span class="sxs-lookup"><span data-stu-id="62544-123">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="62544-124">Associar um certificado SSL a um número de porta</span><span class="sxs-lookup"><span data-stu-id="62544-124">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="62544-125">No Windows Server 2003 ou no Windows XP, use a ferramenta HttpCfg. exe no modo "set" no repositório de protocolo SSL (SSL) para associar o certificado a um número de porta.</span><span class="sxs-lookup"><span data-stu-id="62544-125">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="62544-126">A ferramenta usa a impressão digital para identificar o certificado, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="62544-126">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="62544-127">A opção **-i** tem a sintaxe de `IP` : `port` e instrui a ferramenta para definir o certificado para a porta 8012 do computador.</span><span class="sxs-lookup"><span data-stu-id="62544-127">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="62544-128">Opcionalmente, os quatro zeros que precedem o número também podem ser substituídos pelo endereço IP real do computador.</span><span class="sxs-lookup"><span data-stu-id="62544-128">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="62544-129">A opção **-h** especifica a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="62544-129">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="62544-130">No Windows Vista, use a ferramenta Netsh. exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="62544-130">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="62544-131">O parâmetro **certhash** especifica a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="62544-131">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="62544-132">O parâmetro **ipport** especifica o endereço IP e a porta e funciona exatamente como a opção **-i** da ferramenta Httpcfg. exe descrita.</span><span class="sxs-lookup"><span data-stu-id="62544-132">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="62544-133">O parâmetro **AppID** é um GUID que pode ser usado para identificar o aplicativo proprietário.</span><span class="sxs-lookup"><span data-stu-id="62544-133">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="62544-134">Associar um certificado SSL a um número de porta e a certificados de cliente de suporte</span><span class="sxs-lookup"><span data-stu-id="62544-134">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="62544-135">No Windows Server 2003 ou no Windows XP, para dar suporte a clientes que se autenticam com certificados X. 509 na camada de transporte, siga o procedimento anterior, mas passe um parâmetro de linha de comando adicional para HttpCfg. exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="62544-135">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="62544-136">A opção **-f** tem a sintaxe de `n` onde n é um número entre 1 e 7.</span><span class="sxs-lookup"><span data-stu-id="62544-136">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="62544-137">Um valor de 2, conforme mostrado no exemplo anterior, permite certificados do cliente na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="62544-137">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="62544-138">Um valor de 3 permite certificados do cliente e mapeia esses certificados para uma conta do Windows.</span><span class="sxs-lookup"><span data-stu-id="62544-138">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="62544-139">Consulte a Ajuda do HttpCfg.exe para obter o comportamento de outros valores.</span><span class="sxs-lookup"><span data-stu-id="62544-139">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="62544-140">No Windows Vista, para dar suporte a clientes que se autenticam com certificados X. 509 na camada de transporte, siga o procedimento anterior, mas com um parâmetro adicional, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="62544-140">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="62544-141">Excluir um certificado SSL de um número de porta</span><span class="sxs-lookup"><span data-stu-id="62544-141">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="62544-142">Use a ferramenta HttpCfg.exe ou Netsh.exe para ver as portas e as impressões digitais de todas as associações no computador.</span><span class="sxs-lookup"><span data-stu-id="62544-142">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="62544-143">Para imprimir as informações em disco, use o caractere de redirecionamento ">", conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="62544-143">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="62544-144">No Windows Server 2003 ou no Windows XP, use a ferramenta HttpCfg. exe com as palavras-chave de **exclusão** e **SSL** .</span><span class="sxs-lookup"><span data-stu-id="62544-144">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="62544-145">Use a opção **-i** para especificar o `IP` `port` número: e a opção **-h** para especificar a impressão digital.</span><span class="sxs-lookup"><span data-stu-id="62544-145">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="62544-146">No Windows Vista, use a ferramenta Netsh. exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="62544-146">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="62544-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62544-147">Example</span></span>  

 <span data-ttu-id="62544-148">O código a seguir mostra como criar um serviço auto-hospedado usando o conjunto de classes <xref:System.ServiceModel.WSHttpBinding> para segurança no transporte.</span><span class="sxs-lookup"><span data-stu-id="62544-148">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="62544-149">Ao criar um aplicativo, especifique o número da porta no endereço.</span><span class="sxs-lookup"><span data-stu-id="62544-149">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="62544-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62544-150">See also</span></span>

- [<span data-ttu-id="62544-151">Segurança de transporte de HTTP</span><span class="sxs-lookup"><span data-stu-id="62544-151">HTTP Transport Security</span></span>](http-transport-security.md)
