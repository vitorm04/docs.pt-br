---
title: "Mitigação: verificações de dois-pontos no caminho | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b5e2426fc81c8fd38994a4124cf71af8ec445bfb
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-path-colon-checks"></a>Mitigação: verificações de dois-pontos no caminho
Começando com os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], várias alterações foram feitas para dar suporte aos caminhos anteriormente sem suporte (em termos de comprimento e formato). Em particular, as verificações da sintaxe adequada do separador de unidade (os dois-pontos) foram corrigidas.  
  
## <a name="impact"></a>Impacto  
 Essas alterações bloqueiam alguns caminhos de URI aos quais os métodos <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName> ofereciam suporte anteriormente.  
  
## <a name="mitigation"></a>Redução  
 Para solucionar o problema de um caminho anteriormente aceitável que não tem mais suporte dos métodos <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName>, faça o seguinte:  
  
-   Remova manualmente o esquema de uma URL. Por exemplo, remova `file://` de uma URL.  
  
-   Passe o URI para um construtor <xref:System.Uri> e recupere o valor da propriedade <xref:System.Uri.LocalPath%2A?displayProperty=fullName>.  
  
-   Recuse a normalização do novo caminho definindo a opção `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> como `true`.  
  
    ```xml  
  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
