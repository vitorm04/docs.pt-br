---
title: "Alterações de redirecionamento no .NET Framework 4.6.1 | Microsoft Docs"
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
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6.1
- application compatibility
ms.assetid: 411ad548-30fa-43da-8716-10eccfc839e6
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0adc4a6cae566b6a15c5fa492620abb74b47335b
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="retargeting-changes-in-the-net-framework-461"></a>Alterações de redirecionamento no .NET Framework 4.6.1
Em casos raros, alterações de redirecionamento podem afetar aplicativos recompilados para segmentar o [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. A menos que indicado de outra forma, essas mudanças não afetam os binários direcionados a uma versão anterior do .NET Framework, mas que são executados no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 O [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] inclui alterações de redirecionamento nas seguintes áreas:  
  
-   [Core](#Core)  
  
-   [Contratos de código](#Contracts)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
<a name="Core"></a>   
## <a name="core"></a>Núcleo  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName>|Em aplicativos direcionados a [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões posteriores, o caractere separador do caminho foi alterado de uma barra invertida ("\\") para uma barra ("/") na propriedade <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A> de objetos <xref:System.IO.Compression.ZipArchiveEntry> criados por sobrecargas do método <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName>.|A alteração traz a implementação do .NET em conformidade com a seção 4.4.17.1 da [Especificação de formato de arquivo .ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) e permite que arquivamentos .ZIP sejam descompactados em sistemas não Windows.<br /><br /> No entanto, em aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões posteriores, é possível recusar esse comportamento. Para saber mais, confira [Mitigation: ZipArchiveEntry.FullName Path Separator](../../../docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md) (Mitigação: separador de caminho ZipArchiveEntry.FullName).|Edge|  
  
<a name="Contracts"></a>   
## <a name="code-contracts"></a>Contratos de código  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=fullName> e <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=fullName>, além de chamadas para <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>|Para aplicativos direcionados ao .NET Framework 4.6.1, o regravador emite o aviso do compilador CC1036: "Chamada detectada ao método 'System.String.IsNullOrWhiteSpace(System.String)' sem [Pure] no método..."|Esse é um aviso do compilador, e não um erro do compilador.<br /><br /> Esse comportamento foi abordado em [Problema nº 339 no GitHub](https://github.com/Microsoft/CodeContracts/issues/339). Para eliminar esse aviso, você pode baixar e compilar uma versão atualizada do código-fonte para as ferramentas de Contratos de Código no [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). As informações para download são encontradas no fim da página.|Secundário|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation"></a>Windows Communication Foundation  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName><br /><br /> (namespace <xref:System.IdentityModel.Claims>)|Em aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], se um conjunto de declarações X509 for inicializado de um certificado que tenha várias entradas DNS em seu campo SAN, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> tentará corresponder o argumento `claimType` a todas as entradas DNS.<br /><br /> Em aplicativos direcionados a versões anteriores do .NET Framework, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> tenta corresponder o argumento `claimType` apenas à última entrada DNS.|Essa alteração afeta todos os aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Os aplicativos direcionados a versões anteriores do .NET Framework não são afetados.<br /><br /> No entanto, em aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], é possível recusar esse comportamento. Além disso, para aplicativos direcionados a versões anteriores do .NET Framework, mas que são executados no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], é possível aceitar esse comportamento. Para saber mais, confira [Mitigation: X509CertificateClaimSet.FindClaims Method](../../../docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md) (Mitigação: método X509CertificateClaimSet.FindClaims).|Secundário|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Forms  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> (namespace <xref:System.Windows.Forms>)|Em aplicativos do Windows Forms direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], uma implementação de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> personalizada pode filtrar mensagens quando o método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> é chamado se a implementação <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName>:<br /><br /> <ul><li>Executa uma ou ambas as ações:<br /><br /> <ul><li>Adiciona um filtro de mensagem chamando o método <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.</li><li>Remove um filtro de mensagem chamando o método <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. método.</li></ul></li><li>**E** bombeia mensagens chamando o método <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName>.</li></ul><br /> Essas implementações em aplicativos do Windows Forms direcionados a versões anteriores do .NET Framework geram, em alguns casos, uma exceção <xref:System.IndexOutOfRangeException> quando o método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> é chamado|Essa alteração afeta todos os aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Os aplicativos direcionados a versões anteriores do .NET Framework não são afetados.<br /><br /> No entanto, em aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], é possível recusar esse comportamento. Além disso, para aplicativos direcionados a versões anteriores do .NET Framework, mas que são executados no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], é possível aceitar esse comportamento. Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](../../../docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).|Edge|  
  
## <a name="see-also"></a>Consulte também  
 [Compatibilidade de aplicativos na versão 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
