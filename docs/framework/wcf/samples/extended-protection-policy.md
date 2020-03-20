---
title: Política de proteção estendida
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 3a5b1c7f296c68d407f0217963dec56f53e9a08a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144716"
---
# <a name="extended-protection-policy"></a>Política de proteção estendida
Proteção estendida é uma iniciativa de segurança para proteger contra ataques de homem no meio (MITM). Um ataque MITM é uma ameaça à segurança na qual um MITM pega as credenciais de um cliente e as encaminha para um servidor.  
  
## <a name="demonstrates"></a>Demonstra  
 Proteção estendida  
  
## <a name="discussion"></a>Discussão  
 Quando os aplicativos autenticam usando Kerberos, Digest ou NTLM usando HTTPS, um canal TLS (Transport Level Security, segurança de nível de transporte) é estabelecido primeiro e, em seguida, a autenticação ocorre usando o canal seguro. No entanto, não há vinculação entre a chave de sessão gerada pelo SSL e a chave de sessão gerada durante a autenticação. Qualquer MITM pode se estabelecer entre o cliente e o servidor e começar a encaminhar as solicitações do cliente, mesmo quando o próprio canal de transporte é seguro, pois o servidor não tem como saber se o canal seguro foi estabelecido a partir do cliente ou um MITM. A solução neste cenário é vincular o canal TLS externo com o canal interno de autenticação, de forma que o servidor possa detectar se há um MITM.  
  
> [!NOTE]
> Essa amostra só funciona quando hospedada no IIS e não pode funcionar no Cassini – Visual Studio Development Server porque a Cassini não suporta HTTPS.  
  
> [!NOTE]
> Este recurso está atualmente disponível apenas no Windows 7. As seguintes etapas são específicas do Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instale serviços de informações da Internet a partir do painel de **controle,** **adicionar/remover programas,** **recursos do Windows.**  
  
2. Instale **a autenticação do Windows** em recursos do **Windows,** **Serviços de Informação da Internet,** **Serviços Web mundiais,** **Segurança**e **Autenticação do Windows.**  
  
3. Instale a **ativação HTTP da Windows Communication Foundation** no Windows **Features,** **Microsoft .NET Framework 3.5.1**e **Windows Communication Foundation HTTP Activation**.  
  
4. Essa amostra exige que o cliente estabeleça um canal seguro com o servidor, por isso requer a presença de um certificado de servidor que pode ser instalado no IIS (Internet Information Services, gerente de serviços de informação da Internet).  
  
    1. Abra o Gerenciador do IIS. Abra **certificados do servidor,** que aparece na guia **Exibição de recursos** quando o nó raiz (nome da máquina) for selecionado.  
  
    2. Com o propósito de testar esta amostra, crie um certificado auto-assinado. Se você não quiser que o Internet Explorer indiste sobre o certificado não ser seguro, instale o certificado na loja de autoridade Trusted Certificate Root.  
  
5. Abra o painel **Ações** para o site padrão. Clique **em Editar site,** **vinculações.** Adicione HTTPS como um tipo, se ainda não estiver presente, com a porta número 443. Atribuir o certificado SSL criado na etapa anterior.  
  
6. Construa o serviço. Isso cria um diretório virtual no IIS e copia os arquivos .dll, .svc e .config conforme necessário para que o serviço seja hospedado na Web.  
  
7. Abra o Gerenciador do IIS. Clique com o botão direito do mouse no diretório virtual **(ExtendedProtection),** que foi criado na etapa anterior. Selecione **Converter para aplicativo**.  
  
8. Abra o módulo **de autenticação** no IIS Manager para este diretório virtual e habilite **a Autenticação do Windows**.  
  
9. Abra **configurações avançadas** na **autenticação do Windows** para este diretório virtual e defina-a como **Obrigatório**.  
  
10. Você pode testar o serviço acessando a URL HTTPS a partir de uma janela do navegador (Forneça um nome de domínio totalmente qualificado). Se você quiser acessar esta URL a partir de uma máquina remota, certifique-se de que o firewall está aberto para todas as conexões HTTP e HTTPS recebidas.  
  
11. Abra o arquivo de configuração do cliente e forneça um nome de `<<full_machine_name>>`domínio totalmente qualificado para o atributo de endereço cliente ou ponto final que substitui .  
  
12. Corra com o cliente. O cliente se comunica com o serviço, que estabelece um canal seguro e usa proteção estendida.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
