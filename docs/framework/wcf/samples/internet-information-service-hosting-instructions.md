---
title: "Instruções de hospedagem de serviço de informação de internet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c815ffe88918502f7d040bdeb1ff1b201cec832
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="internet-information-service-hosting-instructions"></a>Instruções de hospedagem de serviço de informação de internet
Para executar os exemplos que são hospedados por serviços de informações da Internet (IIS), você deve garantir que o IIS está instalado corretamente e está em execução.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Para instalar o IIS versão 7.5 no Windows Server 2008 R2  
  
1.  De **Gerenciador do servidor**, selecione **funções.** Em **resumo de funções**, clique em **adicionar funções**.  
  
2.  Clique em **próximo** para exibir o **selecionar funções de servidor** caixa de diálogo.  
  
3.  Selecione **Application Server** do **funções** lista e, em seguida, clique em **próximo** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para o Função de servidor de aplicativos.  
  
4.  Selecione o **servidor Web (IIS)** caixa de seleção. Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar recursos necessários**. Clique em **próximo** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para a função de servidor Web (IIS).  
  
5.  Expanda **ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade de gerenciamento do IIS 6**. Selecione **IIS ferramentas de script 6**. Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar serviços de função necessários**. Clique em **Avançar**.  
  
6.  Se o resumo das seleções estiver correto, clique em **instalar**.  
  
7.  Quando a instalação for concluída, clique em **fechar**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Para instalar o IIS versão 7.5 no Windows 7  
  
1.  Clique em **iniciar**e, em seguida, clique em **painel de controle**.  
  
2.  Abra o **programas** grupo.  
  
3.  Em **programas e recursos**, clique em **ativar ou desativar recursos do Windows**.  
  
4.  O **User Account Control** caixa de diálogo é exibida. Clique em **Continue**.  
  
5.  O **recursos do Windows** caixa de diálogo é exibida. Expanda o item rotulado **Internet Information Services**.  
  
6.  Expanda o item rotulado **serviços da World Wide Web**.  
  
7.  Expanda o item rotulado **recursos de desenvolvimento de aplicativo**.  
  
8.  Verifique se que os seguintes itens são selecionados:  
  
    1.  **Extensibilidade .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Extensões ISAPI**  
  
    4.  **Filtros ISAPI**  
  
9. Sob o item rotulado **serviços da World Wide Web**, expanda **recursos Http comuns**.  
  
10. Certifique-se de **conteúdo estático** está selecionado.  
  
11. Sob o item rotulado **serviços da World Wide Web**, expanda **segurança**.  
  
12. Verifique se **autenticação do Windows** está selecionado.  
  
13. Sob o **Internet Information Services** directory, expanda o item rotulado **ferramentas de gerenciamento da Web**e, em seguida, selecione **Console de gerenciamento IIS**.  
  
14. Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.  
  
15. Sob o **Internet Information Services** directory, expanda o item rotulado **Microsoft .NET Framework 3.5.1**e, em seguida, selecione **ativação de Http do Windows Communication Foundation**.  
  
16. Clique em **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Para instalar o IIS versão 7.0 no Windows Server 2008  
  
1.  De **Gerenciador do servidor**, selecione **funções**. Em **resumo de funções**, clique em **adicionar funções**.  
  
2.  Clique em **próximo** para exibir o **selecionar funções de servidor** caixa de diálogo.  
  
3.  Selecione **Application Server** do **funções** lista e, em seguida, clique em **próximo** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para o Função de servidor de aplicativos.  
  
4.  Selecione **servidor Web (IIS)** caixa de seleção. Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar recursos necessários**. Clique em **próximo** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para a função de servidor Web (IIS).  
  
5.  Expanda **ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade de gerenciamento do IIS 6**. Selecione **IIS ferramentas de script 6**. Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar serviços de função necessários**. Clique em **Avançar**.  
  
6.  Se o resumo das seleções estiver correto, clique em **instalar**.  
  
7.  Quando a instalação for concluída, clique em **fechar**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Para instalar o IIS versão 7.0 no Windows Vista  
  
1.  Clique em Iniciar e, em seguida, clique em Painel de controle.  
  
2.  Selecione o **programas** grupo.  
  
3.  Em **programas e recursos**, clique em **ativar ou desativar recursos do Windows**.  
  
4.  O **User Account Control** caixa de diálogo é exibida. Clique em **Continue**.  
  
5.  O **recursos do Windows** caixa de diálogo é exibida. Expanda o item rotulado **Internet Information Services**.  
  
6.  Expanda o item rotulado **serviços da World Wide Web**.  
  
7.  Expanda o item rotulado **recursos de desenvolvimento de aplicativo**.  
  
8.  Verifique se que os seguintes itens são selecionados:  
  
    1.  **Extensibilidade .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Extensões ISAPI**  
  
    4.  **Filtros ISAPI**  
  
9. Expanda o item rotulado **ferramentas de gerenciamento da Web**e, em seguida, selecione **Console de gerenciamento IIS**.  
  
10. Sob o item rotulado **serviços da World Wide Web**, expanda **recursos Http comuns**.  
  
11. Certifique-se de **conteúdo estático** está selecionado.  
  
12. Sob o item rotulado **serviços da World Wide Web**, expanda **segurança**.  
  
13. Certifique-se de **autenticação do Windows** está selecionado.  
  
14. Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.  
  
15. Expanda o item rotulado **Microsoft .NET Framework 3.0**e, em seguida, selecione **ativação Http do Windows Communication Foundation**.  
  
16. Clique em**Okey**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Para instalar o IIS versão 6.0 no Windows Server 2003  
  
1.  De **Gerenciar servidor**, clique em **adicionar ou remover uma função**e, em seguida, clique em **próximo**.  
  
2.  Selecione **servidor de aplicativos (IIS, ASP.NET)** do **função de servidor** lista e, em seguida, clique em **próximo**.  
  
3.  Selecione **ativar ASP.NET** caixa de seleção e, em seguida, clique em **próximo**.  
  
4.  Se o resumo das seleções estiver correto, clique em Avançar.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Para instalar o IIS versão 5.1 no Windows XP com Service Pack 2 e Service Pack 3 instalado  
  
1.  No painel de controle, clique em **adicionar ou remover programas**.  
  
2.  No **adicionar ou remover programas** caixa de diálogo, clique em **Adicionar/remover componentes do Windows**.  
  
3.  No **Assistente de componentes do Windows**, selecione o **serviços de informações da Internet (IIS)** caixa de seleção e, em seguida, clique em **próximo**.  
  
4.  Se o **arquivos necessários** caixa de diálogo é exibida, insira o disco de instalação do sistema operacional, navegue até a pasta i386 e, em seguida, clique em **Okey**.  
  
5.  Quando a instalação for concluída, clique em **concluir**.  
  
6.  Feche o **adicionar ou remover programas** caixa de diálogo e, em seguida, feche **painel de controle**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Para verificar a instalação do IIS e ASP.NET  
  
1.  Salve o arquivo HTML encontrado no final deste tópico no diretório raiz \InetPub\wwwroot e nomeie-a como Default. aspx.  
  
2.  Abra uma janela do navegador.  
  
3.  Tipo `http://localhost/Default.aspx` na caixa Endereço e pressione ENTER.  
  
4.  Deve aparecer uma página da Web com o texto "Olá, mundo".  
  
> [!NOTE]
>  Cada vez que você instala uma nova versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], é necessário registrar novamente aspnet_isapi como uma extensão de serviço da Web do IIS. Para fazer isso, execute o `aspnet_regiis –I –enable` comando.  
  
## <a name="sample-code"></a>Código de exemplo  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
