---
title: "Mitigação: quadros PNG no objetos de ícone | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9d5088d70397e21cb555c78b2701960ee69bde66
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-png-frames-in-icon-objects"></a>Mitigação: quadros PNG em objetos de ícone
Começando com o .NET Framework 4.6, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> converte com êxito ícones com quadros PNG em objetos <xref:System.Drawing.Bitmap>.  
  
 Em aplicativos direcionados ao .NET Framework 4.5.2 e versões anteriores, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> vai gerar uma exceção <xref:System.ArgumentOutOfRangeException> se o objeto <xref:System.Drawing.Icon> tiver quadros PNG.  
  
## <a name="impact"></a>Impacto  
 Essa alteração afeta aplicativos que são recompilados para direcionamento ao .NET Framework 4.6 e que implementam tratamento especial para a <xref:System.ArgumentOutOfRangeException> que será gerada se um objeto <xref:System.Drawing.Icon> tiver quadros de PNG. Ao executar no .NET Framework 4.6, a conversão é bem-sucedida, uma <xref:System.ArgumentOutOfRangeException> não é mais gerada e, portanto, o manipulador de exceção não é invocado.  
  
### <a name="mitigation"></a>Redução  
 Se esse comportamento for indesejável, será possível reter o comportamento anterior adicionando o seguinte elemento à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:  
  
```  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
  
```  
  
 Se o arquivo app.config já contiver o elemento `AppContextSwitchOverrides`, o novo valor deverá ser mesclado ao atributo `value`, da seguinte forma:  
  
```  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
