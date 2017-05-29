---
title: "Alterações de redirecionamento no .NET Framework 4.7 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes,.NET Framework
- retargeting changes,.NET Framework 4.7
- application compatibility
ms.assetid: d98bf1e3-0017-4933-8e7b-191ac3542fcc
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: fccd83571b47e3c2a6f995893c6260ae91eae517
ms.openlocfilehash: 53c3bc41e319fe122605993d4013e6f04832c89c
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="retargeting-changes-in-the-net-framework-47"></a>Alterações de redirecionamento no .NET Framework 4.7

Em casos raros, alterações de redirecionamento podem afetar aplicativos que são recompilados para serem destinados ao .NET Framework 4.7. Elas não afetam binários que se destinam a uma versão anterior do .NET Framework, mas são executados na versão 4.7. O .NET Framework 4.7 inclui alterações de redirecionamento nas seguintes áreas:  

-   [Core](#Core)  
-   [ASP.NET](#asp) 
-   [WCF (Windows Communication Foundation)](#WCF)  
-   [Windows Presentation Foundation (WPF)](#WPF)
 
 A coluna Escopo nas tabelas a seguir especifica o significado de cada alteração:  
  
-   Principal. Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código. Observe que nenhuma das alterações de redirecionamento entra nessa categoria.  
  
-   Secundário. Uma alteração que afeta um pequeno número de aplicativos ou que exige a modificação secundária do código.  
  
-   Borda. Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.  
  
-   Transparente. Uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.  
  
## <a name="a-namecore--core"></a><a name="Core" /> Core

| Recurso | Alteração | Impacto | Escopo |
|----|----|----|----|
|<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> | Os aplicativos destinados ao .NET Framework 4.6.2 e a versões anteriores esperam que o valor atribuído a essa propriedade seja um <xref:System.IntPtr> no local especificado na memória em que reside o valor de HWND.<br/></br>A partir dos aplicativos destinados ao .NET Framework 4.7, um aplicativo do Windows Forms pode definir o valor dessa propriedade com um código semelhante ao seguinte: <br/><br/>` cspParameters.ParentWindowHandle = form.Handle; ` | Os aplicativos que acham essa alteração de comportamento inconveniente podem recusar o novo comportamento. Da mesma forma, os aplicativos que são destinados a versões anteriores do .NET Framework, mas estão em execução do .NET Framework 4.7 podem aceitar o novo comportamento. Para obter mais informações, consulte [Mitigação: CspParameters.ParentWindowHandle espera um HWND](../../../docs/framework/migration-guide/mitigation-cspparameters-parentwindowhandle-expects-an-hwnd.md). | Secundário |
| Serialização com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> | A partir dos aplicativos destinados ao .NET Framework 4.7, a serialização dos caracteres de controle com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> agora é compatível com o ECMAScript V6 e V8 | Essa alteração está em conformidade com o padrão ECMAScript e deve ter um impacto pequeno. Se isso acontecer, uma opção de compatibilidade estará disponível para restaurar o comportamento anterior. Para obter mais informações, consulte [Mitigação: serialização de caracteres de controle com o DataContractJsonSerializer](../../../docs/framework/migration-guide/mitigation-serialization-control-characters.md)  | Edge |

## <a name="a-nameasp--aspnet"></a><a name="asp" /> ASP.NET

| Recurso  |Alteração  |Impacto | Escopo | 
---------|---------|---------|-----|
Limitação de solicitações simultâneas por sessão | No .NET Framework 4.6.2 e nas versões anteriores, o ASP.NET executa solicitações com a mesma <xref:System.Web.SessionState.HttpSessionState.SessionID%2A> sequencialmente, e o ASP.NET sempre emite a <xref:System.Web.SessionState.HttpSessionState.SessionID%2A> por meio de um cookie por padrão. Se uma página demorar muito tempo para carregar, pressionar <kbd>F5</kbd> do navegador diminuirá significativamente o desempenho do servidor.<br/><br/>A partir do .NET Framework 4.7, um contador acompanha as solicitações enfileiradas e encerra as solicitações quando elas excedem um limite especificado. O valor padrão é 50. Se o limite for alcançado, um aviso será registrado no log de eventos e uma resposta HTTP 500 poderá ser registrada no log do IIS.|Essa alteração pode melhorar o desempenho geral do servidor.<br/><br/>Para restaurar o comportamento antigo, você pode adicionar a seguinte configuração ao arquivo web.config para recusar o novo comportamento.<br/><br/>`<appSettings>`<br/>&nbsp;&nbsp;&nbsp;`<add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>`<br/>`</appSettings>` | Edge |

## <a name="a-namewcf--windows-communication-foundation"></a><a name="WCF" /> Windows Communication Foundation

| Recurso  |Alteração  |Impacto | Escopo | 
---------|---------|---------|-----|
| Segurança de mensagem do WCF | Os aplicativos que são executados no .NET Framework 4.7 ou posterior são capazes de usar o TLS 1.1 e TLS 1.2 na segurança de mensagens do WCF por meio de definições de configuração do aplicativo. Esse é um recurso de aceitação. Por padrão, o suporte para o TLS 1.1 e o TLS 1.2 na segurança de mensagens do WCF é desabilitado. | O comportamento padrão de segurança de mensagens do WCF permanece inalterado. <br/><br/> Para habilitar o suporte para o TLS 1.1 e o TLS 1.2, adicione a seguinte definição de configuração na seção [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo `app.config` ou `web.config`:  <br/><br/>`<runtime>` <br/> &nbsp;&nbsp;&nbsp;`<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;`<br/>&nbsp;&nbsp;&nbsp;`Switch.System.Net.DontEnableSchUseStrongCrypto=false" />`<br/>`</runtime>` | Edge |         

## <a name="a-namewpf--windows-presentation-foundation-wpf"></a><a name="WPF" /> WPF (Windows Presentation Foundation)  

| Recurso | Alteração | Impacto | Escopo |
|---|---|---|---|
| A alocação de espaço do controle <xref:System.Windows.Controls.Grid> para colunas de estrela | A partir dos aplicativos destinados ao .NET Framework 4.7, o WPF substitui o algoritmo que o controle <xref:System.Windows.Controls.Grid> usa para alocar espaço para \*-columns.md) | Para aplicativos destinados às versões do .NET Framework, a partir do .NET Framework 4.7, essa alteração afeta a largura real atribuída a colunas de \* em diversos casos. Se essa alteração for indesejada, o algoritmo anterior poderá continuar a ser aplicado, adicionando uma entrada ao arquivo de configuração do aplicativo. Para obter mais informações, consulte [Mitigação: alocação de espaço do controle de grade para colunas de estrela](../../../docs/framework/migration-guide/mitigation-grid-control.md). | Secundário |
<xref:System.Windows.Media.ImageSourceConverter.ConvertFrom%2A> | Em aplicativos destinados ao .NET Framework 4.6.2 e a versões anteriores, um erro no código de tratamento de exceções do método <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom%2A> faziam com que fosse gerada uma <xref:System.NullReferenceException> em vez da exceção pretendida (como uma <xref:System.IO.DirectoryNotFoundException> ou uma <xref:System.IO.FileNotFoundException>).<br/><br/>A partir dos aplicativos destinados ao .NET Framework 4.7, a exceção correta é gerada.  | Aplicativos destinados ao .NET Framework 4.7 e que dependem do tratamento de uma <xref:System.NullReferenceException> pode restaurar o comportamento anterior adicionando o seguinte à definição de configuração para a seção [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo `app.config`: <br/><br/>`<runtime>`<br/>&nbsp;&nbsp;&nbsp;`<AppContextSwitchOverrides value="Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true"/>`<br/>`</runtime>`| Edge | 
| Suporte de aceitação de uma pilha de toque/caneta com base em `WM_POINTER` | A partir dos aplicativos destinados ao .NET Framework 4.7, o WPF adiciona o suporte para um recurso opcional de toque baseado em WM_POINTER.  | Esse é um recurso de aceitação, que está disponível nos sistemas Windows, a partir da Atualização do Windows 10 para Criadores. Os aplicativos do WPF que não aceitam explicitamente o suporte a toque/caneta com base em ponteiro não são afetados. Para obter mais informações, consulte [Mitigação: suporte a toque e caneta com base em ponteiro](../Topic/Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md). | Edge |
| Classe <xref:System.Printing.PrintQueue> | Começando do .NET Framework 4.7, as APIs de impressão do WPF que usam <xref:System.Printing.PrintQueue> por padrão chamam a API de Pacote de Documentos de Impressão do Windows em vez da API de Impressão XPS que agora foi preterida.<br/><br/>A pilha de impressão antiga continua a funcionar como antes, nas versões mais antigas do Windows. | Nem usuários nem os desenvolvedores devem ver todas as alterações no comportamento ou no uso da API. <br/><br/>Para usar a pilha antiga na Atualização do Windows 10 para Criadores, defina o valor de `UseXpsOMPrinting` `REG_DWORD` da chave do Registro `HKEY_CURRENT_USER\Software\Microsoft.NETFramework\Windows Presentation Foundation\Printing` como 1. | Edge | 
## <a name="see-also"></a>Consulte também
[Compatibilidade de aplicativos no .NET Framework 4.7](Application%20Compatibility%20in%20the%20.NET%20Framework%204.7.md)

