---
title: "Alterações de redirecionamento no .NET Framework 4.5.2 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2be2a828-9052-4738-a965-d4a836cc6384
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 10af942724ce0207bc6e64f1ebabfdcd2d3488bd
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-452"></a>Alterações no redirecionamento no .NET Framework 4.5.2
Em casos raros, alterações de redirecionamento podem afetar aplicativos recompilados direcionados para o .NET Framework 4.5.2. A menos que indicado de outra forma, nas tabelas seguintes essas mudanças não afetam os binários que usam como destino uma versão anterior do .NET Framework, mas que estão sendo executados na versão 4.5.2. O .NET Framework 4.5.2 inclui alterações de redirecionamento nas seguintes áreas:  
  
-   [Entity Framework](#EF)  
  
-   [Windows Forms](#WinForms)  
  
<a name="EF"></a>   
## <a name="entity-framework-retargeting-changes"></a>Alterações de redirecionamento no Entity Framework  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Consultas mais simples ao usar operações limitantes não classificadas|As consultas que produzem instruções `JOIN` e contêm uma chamada para uma operação de limitação sem usar primeiro o <xref:System.Data.Objects.ObjectQuery%601.OrderBy%2A> agora produzem um SQL mais simples. Após a atualização para [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], essas consultas produziram SQLs mais complicados do que as versões anteriores.|Esse recurso está desabilitado por padrão. Se Entity Framework gera instruções `JOIN` adicionais que causam a degradação do desempenho, pode-se habilitar esse recurso adicionando a seguinte entrada na seção `<appSettings>` do arquivo (app.config) de configuração da aplicação:<br /><br /> `<add key="EntityFramework_SimplifyLimitOperations" value="true" />`|Secundário|  
  
<a name="WinForms"></a>   
## <a name="windows-forms-retargeting-changes"></a>Alterações de redirecionamento do Windows Forms  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Recuperando dados no formato HTML da Área de Transferência com o método <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName>|Para aplicativos direcionados ao [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ou que são executados no .NET Framework 4.5.1 ou versões anteriores, <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName> recupera dados formatados em HTML como cadeia de caracteres ASCII. Como resultado, caracteres não ASCII (caracteres cujos códigos ASCII são maiores que 0x7F) são representados por dois caracteres aleatórios. Por exemplo, é (0xE9) é representado por Ã© (0xC3 0xA9).<br /><br /> Para aplicativos direcionados ao [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou posteriores e executados no .NET Framework 4.5.2, <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName> recupera dados formatados em HTML como UTF-8, que representam caracteres maiores que 0x7F corretamente.|Se você tiver implementado uma solução alternativa para o problema de codificação com cadeias de caracteres formatadas em HTML (por exemplo, codificando explicitamente a cadeia de caracteres HTML recuperada da Área de Transferência e enviando-a para o método <xref:System.Text.UTF8Encoding.GetString%2A?displayProperty=fullName>) e está redirecionando seu aplicativo da versão 4 para a versão 4.5, essa solução deverá ser removida.|Secundário|  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-2.md)   
 [Compatibilidade de aplicativos no 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilidade de aplicativos no 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)
