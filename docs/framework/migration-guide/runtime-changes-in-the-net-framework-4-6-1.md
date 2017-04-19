---
title: "Alterações de tempo de execução no .NET Framework 4.6.1 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6.1
- application compatibility
ms.assetid: 9d97421c-5fee-4523-98c9-a158e7e6a1ee
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b8c6ec4d0bad4a769fb4d19a98c9e8a4eda0db78
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-461"></a>Alterações de tempo de execução no .NET Framework 4.6.1
Em casos raros, as alterações de tempo de execução podem afetar aplicativos existentes direcionados a versões anteriores do .NET Framework, mas que são executados em uma versão posterior do tempo de execução do .NET Framework. Elas também incluem diferenças no comportamento entre aplicativos que são executados em diferentes ambientes de tempo de execução do .NET Framework. O [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] inclui alterações nas seguintes áreas:  
  
-   [WCF (Windows Communication Foundation)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Associação WCF ao modo de segurança `TransportWithMessageCredential`|Por padrão, a associação WCF que usa o modo de segurança `TransportWithMessageCredential` não permite mensagens com um cabeçalho "para" não assinado para chaves de segurança assimétricas. Começando com aplicativos que são executados no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], é possível abrandar esse requisito e receber mensagens que não têm cabeçalhos "para" assinados.|Esse é um comportamento de aceitação. Para permitir mensagens com cabeçalhos "para" não assinados, adicione a seguinte definição de configuração à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:<br /><br /> `<runtime>     <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />  </runtime>`<br /><br /> Como esse é um recurso de aceitação, ele não deve afetar o comportamento dos aplicativos existentes.|Edge|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>|Quando um <xref:System.Windows.Controls.ItemsControl> exibe uma coleção usando a virtualização (<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> = `true`) e a rolagem por item (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>), e quando o controle é rolado para exibir um item cuja altura em pixels difere de seus vizinhos, o <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> é iterado por todos os itens na coleção.   A interface do usuário não responde durante essa iteração; se a coleção for grande, isso poderá ser percebido como um travamento.<br /><br /> Essa iteração ocorre em outras circunstâncias, mesmo em versões anteriores do [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Por exemplo, ela ocorre na rolagem por pixel (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>) mediante encontro de um item com uma altura de pixel diferente, bem como nos dados hierárquicos da rolagem por item (como em um controle <xref:System.Windows.Controls.TreeView> ou um <xref:System.Windows.Controls.ItemsControl> com agrupamento habilitado) mediante encontro de um item com um número diferente de itens descendentes de seus vizinhos.<br /><br /> Para o caso de rolagem por item e diferentes alturas de pixel, a iteração foi introduzida no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] para corrigir bugs no layout dos dados hierárquicos.  Ela não será necessária se os dados forem simples (não tiverem hierarquia) e o [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] não fizer isso nesse caso.|Se a iteração ocorrer no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], mas não em versões anteriores – isto é, se <xref:System.Windows.Controls.ItemsControl> for uma lista simples de rolagem por item com itens de diferentes alturas de pixel – haverá duas correções:<br /><br /> Instalar o [.NET Framework 4.6.2](../../../docs/framework/install/guide-for-developers.md).<br /><br /> Instalar o [hotfix HR 1605](https://support.microsoft.com/en-us/kb/3154529) para o [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].|Secundário|  
## <a name="see-also"></a>Consulte também  
 [Compatibilidade de aplicativos na versão 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
