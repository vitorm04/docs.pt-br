---
title: "Mitigação: suporte ao caminho longo"
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
ms.assetid: 3cbe2d77-6e2c-4665-a6c5-7000b9ad6890
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 138e96c3d45b79ccf30f6a3d39f0af26a48c0117
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-long-path-support"></a>Mitigação: suporte ao caminho longo
A partir dos aplicativos destinados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], os métodos de E/S do sistema de arquivos não gera mais automaticamente um <xref:System.IO.PathTooLongException> se um caminho ou nome de arquivo totalmente qualificado ultrapassar 260 (ou `MAX_PATH`) caracteres. Em vez disso, há suporte para caminhos de até 32 mil caracteres.  
  
## <a name="impact"></a>Impacto  
 Os aplicativos recompilados para o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] e que geravam anteriormente um <xref:System.IO.PathTooLongException> automaticamente porque um caminho tinha excedido 260 caracteres agora só gerarão uma <xref:System.IO.PathTooLongException> sob as seguintes condições:  
  
-   O tamanho do caminho é superior a <xref:System.Int16.MaxValue?displayProperty=fullName> (32.767) caracteres.  
  
-   O sistema operacional retorna `COR_E_PATHTOOLONG` ou seu equivalente.  
  
 O comportamento herdado de aplicativos destinados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões anteriores é que o tempo de execução gera automaticamente um <xref:System.IO.PathTooLongException> sempre que um caminho excede 260 caracteres.  
  
## <a name="mitigation"></a>Redução  
 Para aplicativos destinados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], você pode recusar o suporte ao caminho longo, se ele não for desejável, adicionando o seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />   
</runtime>  
```  
  
 Para aplicativos destinados a versões anteriores do .NET Framework mas executados no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou versão posterior, você pode aceitar o suporte ao caminho longo adicionando o seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

