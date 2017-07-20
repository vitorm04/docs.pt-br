---
title: "Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d85c827b414cc94410a921bfae9ce3e1764d22ea
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage
Em aplicativos do Windows Forms direcionados a versões do .NET Framework a partir da [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], uma implementação de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> personalizada pode filtrar mensagens quando o método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> for chamado se a implementação <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName>:  
  
-   Executa uma ou ambas as ações:  
  
    -   Adiciona um filtro de mensagem chamando o método <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.  
  
    -   Remove um filtro de mensagem chamando o método <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. método.  
  
-   **E** bombeia mensagens chamando o método <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName>.  
  
## <a name="impact"></a>Impacto  
 Essa alteração afeta somente os aplicativos do Windows Forms que se destinam a versões do .NET Framework, começando pelo [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Para aplicativos do Windows Forms direcionados a versões anteriores do .NET Framework, essas implementações podem, em alguns casos, lançar uma exceção <xref:System.IndexOutOfRangeException> quando o método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> é chamado  
  
## <a name="mitigation"></a>Redução  
 Se essa alteração for indesejável, os aplicativos que se destinam ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou uma versão posterior, poderão recusá-la adicionando a seguinte definição de configuração à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
```  
  
 Além disso, os aplicativos destinados a versões anteriores do .NET Framework, mas estão sendo executados no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou em uma versão posterior, podem aceitar esse comportamento adicionando a seguinte definição de configuração à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)

