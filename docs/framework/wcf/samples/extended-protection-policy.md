---
title: Política de proteção estendida
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: c2a79798569e308c37bd66bf0bdf8dee0cfa6951
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650053"
---
# <a name="extended-protection-policy"></a>Política de proteção estendida
Proteção estendida é uma iniciativa de segurança para proteger contra ataques man-in-the-middle (MITM). Um ataque MITM é uma ameaça de segurança no qual um MITM usa credenciais do cliente e os encaminha para um servidor.  
  
## <a name="demonstrates"></a>Demonstra  
 Proteção estendida  
  
## <a name="discussion"></a>Discussão  
 Quando os aplicativos se autenticar usando Kerberos ou NTLM usando HTTPS, Digest, primeiro é estabelecer um canal de segurança de nível de transporte (TLS) e, em seguida, a autenticação é feita usando o canal seguro. No entanto, não há nenhuma associação entre a chave de sessão gerada pelo SSL e a chave de sessão gerada durante a autenticação. Qualquer MITM pode estabelecer entre o cliente e o servidor e iniciar encaminhando as solicitações do cliente, mesmo quando o canal de transporte é seguro, pois o servidor tem que não há como saber se o canal seguro foi estabelecido do cliente ou um MITM. A solução neste cenário é associar o canal TLS externo com o canal de autenticação interno, de modo que o servidor pode detectar se há um MITM.  
  
> [!NOTE]
>  Este exemplo só funciona quando hospedado no IIS e não pode funcionar em Cassini – Visual Studio Development Server, pois o Cassini não dá suporte a HTTPS.  
  
> [!NOTE]
>  Este recurso só está disponível no Windows 7. As etapas a seguir são específicas para o Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instalar serviços de informações da Internet da **painel de controle**, **adicionar ou remover programas**, **recursos do Windows**.  
  
2. Instale **autenticação do Windows** na **recursos do Windows**, **serviços de informações da Internet**, **serviços da World Wide Web**,  **Segurança**, e **autenticação do Windows**.  
  
3. Instale **ativação do Windows Communication Foundation HTTP** na **recursos do Windows**, **Microsoft .NET Framework 3.5.1**, e **comunicação do Windows Ativação HTTP do Foundation**.  
  
4. Este exemplo requer que o cliente estabelecer um canal seguro com o servidor, portanto, ele exige a presença de um certificado de servidor que pode ser instalado do Gerenciador de serviços de informações da Internet (IIS).  
  
    1. Abra o Gerenciador do IIS. Abra **certificados de servidor**, que aparece na **modo de exibição de recurso** guia quando o nó raiz (nome da máquina) é selecionado.  
  
    2. Para fins de teste neste exemplo, crie um certificado autoassinado. Se não desejar o Internet Explorer para avisá-lo sobre o certificado não ser seguro, instale o certificado no repositório de autoridade de certificado de raiz confiável.  
  
5. Abra o **ações** painel para o site da Web padrão. Clique em **Editar Site**, **associações**. Adicionar HTTPS como um tipo se não estiver presente, com o número da porta 443. Atribua o certificado SSL criado na etapa anterior.  
  
6. Crie o serviço. Isso cria um diretório virtual no IIS e copia os arquivos. dll,. svc e. config, conforme necessário para o serviço esteja hospedado na Web.  
  
7. Abra o Gerenciador do IIS. O diretório virtual com o botão direito (**ExtendedProtection**), que foi criado na etapa anterior. Selecione **converter em aplicativo**.  
  
8. Abra o **autenticação** módulo no Gerenciador do IIS para este diretório virtual e habilite **autenticação do Windows**.  
  
9. Abra **configurações avançadas** sob **autenticação do Windows** para este diretório virtual e defina-a como **necessária**.  
  
10. Você pode testar o serviço acessando a URL HTTPS de uma janela do navegador (Forneça um nome de domínio totalmente qualificado). Se você quiser acessar essa URL de um computador remoto, certifique-se de que o firewall está aberto, todas as conexões de entrada HTTP e HTTPS.  
  
11. Abra o arquivo de configuração do cliente e forneça um nome de domínio totalmente qualificado para o atributo de endereço de cliente ou o ponto de extremidade que substitui `<<full_machine_name>>`.  
  
12. Execute o cliente. O cliente se comunica com o serviço, que estabelece um canal seguro e usa a proteção estendida.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
