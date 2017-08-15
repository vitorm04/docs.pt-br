---
title: Instalar o .NET Framework 3.5 no Windows 8, no Windows 8.1 e no Windows 10
ms.date: 05/26/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework 3.5, installing on Windows 8
- Windows 8, installing .NET Framework 3.5
ms.assetid: 3eab3eb4-4573-42ac-98f8-36fb2c22c7d5
caps.latest.revision: 69
author: mairaw
ms.author: mairaw
ms.translationtype: HT
ms.sourcegitcommit: 20b0c1b36f705deb2f46ef4ab23653f829faf7ca
ms.openlocfilehash: 8a0395e28c01363eed27f327ea623feb4832c844
ms.contentlocale: pt-br
ms.lasthandoff: 08/08/2017

---

# <a name="install-the-net-framework-35-on-windows-8-windows-81-and-windows-10"></a>Instalar o .NET Framework 3.5 no Windows 8, no Windows 8.1 e no Windows 10

O .NET Framework é parte integrante de vários aplicativos em execução no Windows e fornece funcionalidades comuns para que esses aplicativos sejam executados. Para desenvolvedores, o .NET Framework fornece um modelo consistente de programação para a criação de aplicativos. Se você estiver usando o sistema operacional Windows, o .NET Framework talvez já esteja instalado em seu computador. Especificamente, o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] está incluído no [!INCLUDE[win8](../../../includes/win8-md.md)], o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] está incluído no [!INCLUDE[win81](../../../includes/win81-md.md)] e o [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] está incluído no Windows 10.  
  
O .NET Framework 3.5, no entanto, não vem automaticamente instalado com o [!INCLUDE[win8](../../../includes/win8-md.md)], o [!INCLUDE[win81](../../../includes/win81-md.md)] ou o Windows 10, e deve ser habilitado separadamente para executar aplicativos que dependem dele. Isso deve ocorrer por meio do Windows Update, que pode ser chamado de três maneiras. Todas elas exigem uma conexão com a Internet:  
  
- [Instalação do .NET Framework 3.5 sob demanda](#OnDemand)  
  
- [Habilitar o .NET Framework 3.5 no Painel de Controle](#ControlPanel)  
  
- [Baixar o instalador do .NET Framework 3.5](http://www.microsoft.com/en-us/download/details.aspx?id=21) (Observação: isso não baixa o .NET Framework diretamente; ele é um instalador que invoca o Windows Update.)  
  
Durante a instalação, você pode encontrar o erro 0x800f0906, 0x800f0907 ou 0x800f081f, que se referem ao [Erro de instalação do .NET Framework 3.5: 0x800f0906, 0x800f0907 ou 0x800f081f](https://support.microsoft.com/en-us/kb/2734782). Observe que eles podem ser resolvidos instalando a [Atualização de segurança 3005628](https://support.microsoft.com/kb/3005628).  
  
Se qualquer um dos métodos acima falhar ou se você não tiver uma conexão com a Internet, use a mídia de instalação do Windows. Para obter detalhes, veja o Método 3 do erro 0x800f0906 no [artigo Erro de instalação do .NET Framework 3.5](https://support.microsoft.com/en-us/kb/2734782). Se você não tiver a mídia de instalação, confira [Criar mídia para Windows 8.1](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0).  
  
**Observações importantes:**
  
- Em geral, não desinstale nenhuma versão do .NET Framework de seu computador. Aplicativos diferentes dependem de versões diferentes do Framework e várias versões do .NET Framework podem ser carregadas em um único computador ao mesmo tempo.  
  
- O .NET Framework 3.5 também é usado por aplicativos compilados para as versões 2.0 e 3.0.  
  
- Instalar um pacote de idiomas do Windows antes de instalar o .NET Framework 3.5 poderá causar a falha da instalação do .NET Framework 3.5. Instale o .NET Framework 3.5 antes de instalar qualquer pacote de idiomas do Windows.  
  
- O Windows CardSpace não está disponível com o .NET Framework 3.5 no [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
- Devido a complicações no modo de instalação do .NET Framework 3.5, infelizmente não é possível fornecer um instalador autônomo e separado que possa ser executado independentemente do Windows Update. Se todos os outros métodos falharem, recorra à mídia de instalação conforme descrito anteriormente.  
  
<a name="OnDemand"></a>   
## <a name="install-the-net-framework-35-on-demand"></a>Instalação do .NET Framework 3.5 sob demanda

Se um aplicativo exigir o .NET Framework 3.5, mas não encontrar essa versão habilitada no seu computador, ele exibirá a caixa de mensagem a seguir, durante a instalação ou quando você executar o aplicativo pela primeira vez. Na caixa de mensagem, escolha **Instalar este recurso** para habilitar o .NET Framework 3.5. Essa opção exige uma conexão com a Internet.  
  
![Caixa de diálogo para instalação do 3.5 no Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
  
<a name="ControlPanel"></a>   
## <a name="enable-the-net-framework-35-in-control-panel"></a>Habilitar o .NET Framework 3.5 no Painel de Controle

Você pode habilitar o .NET Framework 3.5 por meio do Painel de Controle. Essa opção exige uma conexão com a Internet.  
  
1. Pressione a tecla Windows ![logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no teclado. Digite "Recursos do Windows" e pressione Enter. Isso abre a caixa de diálogo **Ativar ou desativar recursos do Windows**. Como alternativa, abra o Painel de Controle, clique nos itens de **Programas** e selecione **Ativar ou desativar recursos do Windows** em **Programas e Recursos**.  
  
2. Marque a caixa de seleção **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0)**, selecione **OK** e reinicialize o computador, se isso for solicitado.  
  
Não é necessário selecionar os itens filho para **ativação HTTP do WCF (Windows Communication Foundation)**, a menos que você seja um desenvolvedor que exija funcionalidade de mapeamento do manipulador e de script do WCF.
  
## <a name="see-also"></a>Consulte também

[Guia de instalação](../../../docs/framework/get-started/index.md)

