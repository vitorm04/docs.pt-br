---
title: Política de proteção estendida
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 00d1500b271625addde4499bc62b5ed4d689caf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="extended-protection-policy"></a>Política de proteção estendida
Proteção estendida é uma iniciativa de segurança para proteger contra ataques man-in-the-middle (MITM). Um ataque MITM é uma ameaça de segurança no qual um MITM usa credenciais do cliente e as encaminha para um servidor.  
  
## <a name="demonstrates"></a>Demonstra  
 Proteção estendida  
  
## <a name="discussion"></a>Discussão  
 Quando aplicativos autenticarem usando Kerberos, Digest ou NTLM usando HTTPS, primeiro é estabelecer um canal de segurança de nível de transporte (TLS) e, em seguida, a autenticação é feita usando o canal seguro. No entanto, não há nenhuma associação entre a chave de sessão gerado pelo SSL e a chave de sessão gerada durante a autenticação. Qualquer MITM pode estabelecer entre o cliente e o servidor e iniciar a encaminhar as solicitações do cliente, mesmo quando o canal de transporte é seguro, porque o servidor não tem como saber se o canal seguro de estabelecimento do cliente ou um MITM. A solução neste cenário é associar o canal TLS externo com o canal de autenticação interno, de modo que o servidor pode detectar se há um MITM.  
  
> [!NOTE]
>  Este exemplo só funciona quando hospedados no IIS e não funciona nos Cassini – servidor de desenvolvimento do Visual Studio como Cassini não dá suporte a HTTPS.  
  
> [!NOTE]
>  Este recurso só está disponível no Windows 7. As etapas a seguir são específicas para o Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar os serviços de informações da Internet de **painel de controle**, **adicionar ou remover programas**, **recursos do Windows**.  
  
2.  Instalar **autenticação do Windows** na **recursos do Windows**, **serviços de informações da Internet**, **serviços da World Wide Web**,  **Segurança**, e **autenticação do Windows**.  
  
3.  Instalar **ativação do Windows Communication Foundation HTTP** na **recursos do Windows**, **do Microsoft .NET Framework 3.5.1**, e **comunicação do Windows Ativação de base HTTP**.  
  
4.  Este exemplo requer que o cliente estabelecer um canal seguro com o servidor, isso requer a presença de um certificado de servidor que pode ser instalado do Gerenciador de serviços de informações da Internet (IIS).  
  
    1.  Abra o Gerenciador do IIS. Abra **certificados de servidor**, que aparece no **exibição do recurso** guia quando o nó raiz (nome do computador) é selecionado.  
  
    2.  Com a finalidade de testar este exemplo, crie um certificado autoassinado. Se não desejar o Internet Explorer para solicitar que você sobre o certificado não está sendo seguro, instale o certificado no repositório de autoridade raiz confiável do certificado.  
  
5.  Abra o **ações** painel para o site da Web padrão. Clique em **Editar Site**, **associações**. Adicionar HTTPS como um tipo se não estiver presente, com o número da porta 443. Atribua o certificado SSL criado na etapa anterior.  
  
6.  O serviço de compilação. Isso cria um diretório virtual no IIS e copia os arquivos. dll,. svc e. config, conforme necessário para o serviço Web hospedado.  
  
7.  Abra o Gerenciador do IIS. Clique com botão direito no diretório virtual (**ExtendedProtection**), que foi criado na etapa anterior. Selecione **converter em aplicativo**.  
  
8.  Abra o **autenticação** módulo no Gerenciador do IIS para este diretório virtual e habilitar **autenticação do Windows**.  
  
9. Abra **configurações avançadas** em **autenticação do Windows** para este diretório virtual e defina-a como **necessária**.  
  
10. Você pode testar o serviço acessando a URL HTTPS em uma janela de navegador (Forneça um nome de domínio totalmente qualificado). Se você quiser acessar essa URL de um computador remoto, certifique-se de que o firewall está aberto todas as conexões de entrada HTTP e HTTPS.  
  
11. Abra o arquivo de configuração do cliente e forneça um nome de domínio totalmente qualificado para o atributo de endereço de cliente ou o ponto de extremidade que substitui `<<full_machine_name>>`.  
  
12. Execute o cliente. O cliente se comunica com o serviço, que estabelece um canal seguro e usa a proteção estendida.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
