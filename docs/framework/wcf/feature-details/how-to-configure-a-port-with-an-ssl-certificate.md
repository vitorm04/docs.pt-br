---
title: 'Como: configurar uma porta com um certificado SSL'
description: Saiba como configurar uma porta com um certificado X. 509, necessário para um serviço WCF auto-hospedado com a classe WSHttpBinding usando a segurança de transporte.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 619a893e0973f6691e32446d75f101201a0b6799
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556376"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="1cc99-103">Como: configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="1cc99-103">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="1cc99-104">Ao criar um serviço de Windows Communication Foundation (WCF) auto-hospedado com a <xref:System.ServiceModel.WSHttpBinding> classe que usa a segurança de transporte, você também deve configurar uma porta com um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="1cc99-104">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="1cc99-105">Se você estiver criando um serviço auto-hospedado, você poderá hospedá-lo serviço no IIS (Serviços de Informações da Internet).</span><span class="sxs-lookup"><span data-stu-id="1cc99-105">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="1cc99-106">Para obter mais informações, consulte [segurança de transporte http](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="1cc99-106">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="1cc99-107">Para configurar uma porta, a ferramenta usada depende do sistema operacional que está sendo executado no computador.</span><span class="sxs-lookup"><span data-stu-id="1cc99-107">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="1cc99-108">Se você estiver executando o Windows Server 2003, use a ferramenta HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="1cc99-108">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="1cc99-109">No Windows Server 2003, essa ferramenta está instalada.</span><span class="sxs-lookup"><span data-stu-id="1cc99-109">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="1cc99-110">Para obter mais informações, consulte a [visão geral do Httpcfg](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="1cc99-110">For more information, see [Httpcfg Overview](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="1cc99-111">A [documentação das ferramentas de suporte do Windows](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explica a sintaxe da ferramenta de Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="1cc99-111">The [Windows Support Tools documentation](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="1cc99-112">Se você estiver executando o Windows Vista, use a ferramenta Netsh.exe que já está instalada.</span><span class="sxs-lookup"><span data-stu-id="1cc99-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1cc99-113">A modificação de certificados armazenados no computador requer privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="1cc99-113">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="1cc99-114">Determinar como as portas são configuradas</span><span class="sxs-lookup"><span data-stu-id="1cc99-114">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="1cc99-115">No Windows Server 2003 ou no Windows XP, use a ferramenta HttpCfg.exe para exibir a configuração da porta atual, usando os comutadores **SSL** e de **consulta** , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cc99-115">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="1cc99-116">No Windows Vista, use a ferramenta Netsh.exe para exibir a configuração da porta atual, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cc99-116">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="1cc99-117">Obter a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="1cc99-117">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="1cc99-118">Use o snap-in do MMC dos Certificados para localizar um certificado X.509 cuja finalidade seja a autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="1cc99-118">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="1cc99-119">Para saber mais, consulte [Como Exibir Certificados com o Snap-in do MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="1cc99-119">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="1cc99-120">Para acessar a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="1cc99-120">Access the certificate's thumbprint.</span></span> <span data-ttu-id="1cc99-121">Para saber mais, confira [Como recuperar a impressão digital de um certificado](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="1cc99-121">For more information, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="1cc99-122">Copie a impressão digital do certificado em um editor de texto, como o Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="1cc99-122">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="1cc99-123">Remova todos os espaços entre os caracteres hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="1cc99-123">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="1cc99-124">Uma maneira de fazer isso é usar o recurso localizar e substituir do editor de texto e substituir cada espaço com um caractere nulo.</span><span class="sxs-lookup"><span data-stu-id="1cc99-124">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="1cc99-125">Associar um certificado SSL a um número de porta</span><span class="sxs-lookup"><span data-stu-id="1cc99-125">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="1cc99-126">No Windows Server 2003 ou no Windows XP, use a ferramenta HttpCfg.exe no modo "set" no repositório de protocolo SSL (SSL) para associar o certificado a um número de porta.</span><span class="sxs-lookup"><span data-stu-id="1cc99-126">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="1cc99-127">A ferramenta usa a impressão digital para identificar o certificado, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="1cc99-127">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="1cc99-128">A opção **-i** tem a sintaxe de `IP` : `port` e instrui a ferramenta para definir o certificado para a porta 8012 do computador.</span><span class="sxs-lookup"><span data-stu-id="1cc99-128">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="1cc99-129">Opcionalmente, os quatro zeros que precedem o número também podem ser substituídos pelo endereço IP real do computador.</span><span class="sxs-lookup"><span data-stu-id="1cc99-129">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="1cc99-130">A opção **-h** especifica a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="1cc99-130">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="1cc99-131">No Windows Vista, use a ferramenta Netsh.exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cc99-131">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="1cc99-132">O parâmetro **certhash** especifica a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="1cc99-132">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="1cc99-133">O parâmetro **ipport** especifica o endereço IP e a porta e funciona exatamente como a opção **-i** da ferramenta de Httpcfg.exe descrita.</span><span class="sxs-lookup"><span data-stu-id="1cc99-133">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="1cc99-134">O parâmetro **AppID** é um GUID que pode ser usado para identificar o aplicativo proprietário.</span><span class="sxs-lookup"><span data-stu-id="1cc99-134">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="1cc99-135">Associar um certificado SSL a um número de porta e a certificados de cliente de suporte</span><span class="sxs-lookup"><span data-stu-id="1cc99-135">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="1cc99-136">No Windows Server 2003 ou no Windows XP, para dar suporte a clientes que se autenticam com certificados X. 509 na camada de transporte, siga o procedimento anterior, mas passe um parâmetro de linha de comando adicional para HttpCfg.exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cc99-136">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="1cc99-137">A opção **-f** tem a sintaxe de `n` onde n é um número entre 1 e 7.</span><span class="sxs-lookup"><span data-stu-id="1cc99-137">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="1cc99-138">Um valor de 2, conforme mostrado no exemplo anterior, permite certificados do cliente na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="1cc99-138">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="1cc99-139">Um valor de 3 permite certificados do cliente e mapeia esses certificados para uma conta do Windows.</span><span class="sxs-lookup"><span data-stu-id="1cc99-139">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="1cc99-140">Consulte a Ajuda do HttpCfg.exe para obter o comportamento de outros valores.</span><span class="sxs-lookup"><span data-stu-id="1cc99-140">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="1cc99-141">No Windows Vista, para dar suporte a clientes que se autenticam com certificados X. 509 na camada de transporte, siga o procedimento anterior, mas com um parâmetro adicional, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cc99-141">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="1cc99-142">Excluir um certificado SSL de um número de porta</span><span class="sxs-lookup"><span data-stu-id="1cc99-142">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="1cc99-143">Use a ferramenta HttpCfg.exe ou Netsh.exe para ver as portas e as impressões digitais de todas as associações no computador.</span><span class="sxs-lookup"><span data-stu-id="1cc99-143">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="1cc99-144">Para imprimir as informações em disco, use o caractere de redirecionamento ">", conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cc99-144">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="1cc99-145">No Windows Server 2003 ou no Windows XP, use a ferramenta HttpCfg.exe com as palavras-chave **delete** e **SSL** .</span><span class="sxs-lookup"><span data-stu-id="1cc99-145">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="1cc99-146">Use a opção **-i** para especificar o `IP` `port` número: e a opção **-h** para especificar a impressão digital.</span><span class="sxs-lookup"><span data-stu-id="1cc99-146">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="1cc99-147">No Windows Vista, use a ferramenta Netsh.exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cc99-147">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="1cc99-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cc99-148">Example</span></span>  

 <span data-ttu-id="1cc99-149">O código a seguir mostra como criar um serviço auto-hospedado usando o conjunto de classes <xref:System.ServiceModel.WSHttpBinding> para segurança no transporte.</span><span class="sxs-lookup"><span data-stu-id="1cc99-149">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="1cc99-150">Ao criar um aplicativo, especifique o número da porta no endereço.</span><span class="sxs-lookup"><span data-stu-id="1cc99-150">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1cc99-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="1cc99-151">See also</span></span>

- [<span data-ttu-id="1cc99-152">Segurança de transporte de HTTP</span><span class="sxs-lookup"><span data-stu-id="1cc99-152">HTTP Transport Security</span></span>](http-transport-security.md)
