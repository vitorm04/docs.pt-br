---
title: Instruções de hospedagem de serviço de informação de internet
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: f5aa276bc1178f3e7c61af7505fcf54df8b934e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954850"
---
# <a name="internet-information-service-hosting-instructions"></a>Instruções de hospedagem de serviço de informação de internet
Para executar os exemplos que são hospedados por serviços de informações da Internet (IIS), certifique-se de que o IIS está instalado corretamente e está em execução.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Para instalar o IIS versão 7.5 no Windows Server 2008 R2  
  
1. Partir **Gerenciador de servidores**, selecione **funções.** Sob **resumo de funções**, clique em **adicionar funções**.  
  
2. Clique em **próxima** para exibir o **selecionar funções de servidor** caixa de diálogo.  
  
3. Selecione **servidor de aplicativos** da **funções** e, em seguida, clique **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para o Função de servidor de aplicativos.  
  
4. Selecione o **servidor Web (IIS)** caixa de seleção. Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar recursos necessários**. Clique em **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para a função de servidor Web (IIS).  
  
5. Expandir **as ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade com gerenciamento do IIS 6**. Selecione **IIS ferramentas de script 6**. Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar serviços de função necessários**. Clique em **Avançar**.  
  
6. Se o resumo das seleções estiver correto, clique em **instalar**.  
  
7. Quando a instalação for concluída, clique em **fechar**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Para instalar o IIS versão 7.5 no Windows 7  
  
1. Clique em **inicie**e, em seguida, clique em **painel de controle**.  
  
2. Abra o **programas** grupo.  
  
3. Sob **programas e recursos**, clique em **ativar ou desativar recursos do Windows**.  
  
4. O **User Account Control** caixa de diálogo é exibida. Clique em **Continue**.  
  
5. O **recursos do Windows** caixa de diálogo é exibida. Expanda o item rotulado **serviços de informações da Internet**.  
  
6. Expanda o item rotulado **serviços da World Wide Web**.  
  
7. Expanda o item rotulado **recursos de desenvolvimento de aplicativo**.  
  
8. Verifique se que os seguintes itens estão selecionados:  
  
    1. **Extensibilidade .NET**  
  
    2. **ASP.NET**  
  
    3. **Extensões ISAPI**  
  
    4. **Filtros ISAPI**  
  
9. Sob o item rotulado **serviços da World Wide Web**, expanda **recursos Http comuns**.  
  
10. Certifique-se **conteúdo estático** está selecionado.  
  
11. Sob o item rotulado **serviços da World Wide Web**, expanda **segurança**.  
  
12. Certifique-se de que **autenticação do Windows** está selecionado.  
  
13. Sob o **serviços de informações da Internet** diretório, expanda o item rotulado **ferramentas de gerenciamento da Web**e, em seguida, selecione **Console de gerenciamento do IIS**.  
  
14. Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.  
  
15. Sob o **serviços de informações da Internet** diretório, expanda o item rotulado **Microsoft .NET Framework 3.5.1**e, em seguida, selecione **Windows Communication Foundation Http Activation**.  
  
16. Clique em **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Para instalar o IIS versão 7.0 no Windows Server 2008  
  
1. Partir **Gerenciador de servidores**, selecione **funções**. Sob **resumo de funções**, clique em **adicionar funções**.  
  
2. Clique em **próxima** para exibir o **selecionar funções de servidor** caixa de diálogo.  
  
3. Selecione **servidor de aplicativos** da **funções** e, em seguida, clique **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para o Função de servidor de aplicativos.  
  
4. Selecione **servidor Web (IIS)** caixa de seleção. Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar recursos necessários**. Clique em **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para a função de servidor Web (IIS).  
  
5. Expandir **as ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade com gerenciamento do IIS 6**. Selecione **IIS ferramentas de script 6**. Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar serviços de função necessários**. Clique em **Avançar**.  
  
6. Se o resumo das seleções estiver correto, clique em **instalar**.  
  
7. Quando a instalação for concluída, clique em **fechar**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Para instalar o IIS versão 7.0 no Windows Vista  
  
1. Clique em Iniciar e, em seguida, clique em Painel de controle.  
  
2. Selecione o **programas** grupo.  
  
3. Sob **programas e recursos**, clique em **ativar ou desativar recursos do Windows**.  
  
4. O **User Account Control** caixa de diálogo é exibida. Clique em **Continue**.  
  
5. O **recursos do Windows** caixa de diálogo é exibida. Expanda o item rotulado **serviços de informações da Internet**.  
  
6. Expanda o item rotulado **serviços da World Wide Web**.  
  
7. Expanda o item rotulado **recursos de desenvolvimento de aplicativo**.  
  
8. Verifique se que os seguintes itens estão selecionados:  
  
    1. **Extensibilidade .NET**  
  
    2. **ASP.NET**  
  
    3. **Extensões ISAPI**  
  
    4. **Filtros ISAPI**  
  
9. Expanda o item rotulado **as ferramentas de gerenciamento da Web**e, em seguida, selecione **Console de gerenciamento IIS**.  
  
10. Sob o item rotulado **serviços da World Wide Web**, expanda **recursos Http comuns**.  
  
11. Certifique-se **conteúdo estático** está selecionado.  
  
12. Sob o item rotulado **serviços da World Wide Web**, expanda **segurança**.  
  
13. Certifique-se **autenticação do Windows** está selecionado.  
  
14. Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.  
  
15. Expanda o item rotulado **Microsoft .NET Framework 3.0**e, em seguida, selecione **Windows Communication Foundation Http Activation**.  
  
16. Clique em **OK**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Para instalar o IIS versão 6.0 no Windows Server 2003  
  
1. Partir **gerenciar o servidor**, clique em **adicionar ou remover uma função**e, em seguida, clique em **próxima**.  
  
2. Selecione **servidor de aplicativos (IIS, ASP.NET)** da **função de servidor** e, em seguida, clique **próxima**.  
  
3. Selecione **ativar ASP.NET** caixa de seleção e, em seguida, clique em **próxima**.  
  
4. Se o resumo das seleções estiver correto, clique em Avançar.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Para instalar o IIS versão 5.1 no Windows XP com Service Pack 2 e Service Pack 3 instalado  
  
1. No painel de controle, clique em **adicionar ou remover programas**.  
  
2. No **adicionar ou remover programas** caixa de diálogo, clique em **Adicionar/remover componentes do Windows**.  
  
3. No **Assistente de componentes do Windows**, selecione o **serviços de informações da Internet (IIS)** caixa de seleção e, em seguida, clique em **próxima**.  
  
4. Se o **arquivos necessários** caixa de diálogo é exibida, insira o disco de instalação do sistema operacional, navegue até a pasta i386 e, em seguida, clique em **Okey**.  
  
5. Quando a instalação for concluída, clique em **concluir**.  
  
6. Feche o **adicionar ou remover programas** caixa de diálogo e, em seguida, feche **painel de controle**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Para verificar a instalação do IIS e ASP.NET  
  
1. Salve o arquivo HTML encontrado no final deste tópico no diretório raiz \InetPub\wwwroot e nomeie-a como Default. aspx.  
  
2. Abra uma janela do navegador.  
  
3. Tipo `http://localhost/Default.aspx` na caixa de endereço e pressione ENTER.  
  
4. Uma página da Web com o texto "Hello World" deve aparecer.  
  
> [!NOTE]
>  Cada vez que você instala uma nova versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], é necessário registrar novamente aspnet_isapi como uma extensão de serviço da Web do IIS. Para fazer isso, emita o `aspnet_regiis –I –enable` comando.  
  
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
