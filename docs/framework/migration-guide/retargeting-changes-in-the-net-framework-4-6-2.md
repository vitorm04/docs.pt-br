---
title: "Alterações de redirecionamento no .NET Framework 4.6.2 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6.2
- application compatibility
ms.assetid: 76dc6849-8210-4e41-8731-20828c98b282
caps.latest.revision: 26
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 229ccf3fa4ff1029334641da350cfd040e4b286e
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="retargeting-changes-in-the-net-framework-462"></a>Alterações de redirecionamento no .NET Framework 4.6.2
Em casos raros, alterações de redirecionamento podem afetar aplicativos recompilados para segmentar o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Elas não afetam binários que se destinam a uma versão anterior do .NET Framework, mas são executados na versão 4.6.2. O [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] inclui alterações de redirecionamento nas seguintes áreas:  
  
-   [Core](#Core)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
 A coluna Escopo nas tabelas a seguir especifica o significado de cada alteração:  
  
-   Principal. Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código. Observe que nenhuma das alterações de redirecionamento entra nessa categoria.  
  
-   Secundário. Uma alteração que afeta um pequeno número de aplicativos ou que exige a modificação secundária do código.  
  
-   Borda. Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.  
  
-   Transparente. Uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.  
  
<a name="Core"></a>   
## <a name="core"></a>Núcleo  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Suporte a caminho longo|Começando com os aplicativos que são direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], há suporte para os caminhos longos (de até 32 mil caracteres), e a limitação de 260 caracteres (ou `MAX_PATH`) em comprimentos de caminho foi removida.|Em aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], os caminhos de código que anteriormente geravam uma <xref:System.IO.PathTooLongException> podem não gerar mais uma exceção. Para saber mais, confira [Mitigation: Long Path Support](~/docs/framework/migration-guide/mitigation-long-path-support.md) (Mitigação: suporte ao caminho longo).|Secundário|  
|Normalização de caminho|Começando com os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], o modo no qual os caminhos são normalizados mudou para deferir ao sistema operacional e fornecer melhor acesso aos caminhos de dispositivos DOS.|As alterações possibilitam acessar caminhos de dispositivo válidos que anteriormente não tinham suporte. Para saber mais, confira [Mitigation: Path Normalization](~/docs/framework/migration-guide/mitigation-path-normalization.md) (Mitigação: normalização de caminho).|Secundário|  
|<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName>|Começando com os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], várias alterações foram feitas para dar suporte aos caminhos anteriormente sem suporte (em termos de comprimento e formato). Em particular, as verificações da sintaxe adequada do separador de unidade (os dois-pontos) foram corrigidas.|Essas alterações bloqueiam alguns caminhos de URI aos quais esses dois métodos anteriormente davam suporte. Para saber mais, confira [Mitigation: Path Colon Checks](~/docs/framework/migration-guide/mitigation-path-colon-checks.md) (Mitigação: verificações de dois-pontos do caminho).|Edge|  
|Construtor <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName>|A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> criada por uma chamada para o método <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> é uma nova instância <xref:System.Security.Claims.ClaimsIdentity>. Nas versões anteriores do .NET Framework, o <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> é uma referência existente.|Em alguns casos, a comparação entre a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> e a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> do <xref:System.Security.Principal.IIdentity> do construtor retorna resultados diferentes.<br /><br /> Para saber mais, confira [Mitigation: ClaimsIdentity Constructor](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md) (Mitigação: construtor ClaimsIdentity).|Edge|  
|<xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor%2A?displayProperty=fullName>|Começando com os aplicativos direcionados para [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], o descriptografador <xref:System.Security.Cryptography.AesCryptoServiceProvider> fornece uma transformação reutilizável.   Após uma chamada para <xref:System.Security.Cryptography.ICryptoTransform.TransformFinalBlock%2A>, a transformação é reinicializada e pode ser reutilizada.<br /><br /> Em aplicativos direcionados a versões anteriores do .NET Framework, a tentativa de reutilizar o descriptografador chamando <xref:System.Security.Cryptography.ICryptoTransform.TransformBlock%2A> após uma chamada para <xref:System.Security.Cryptography.ICryptoTransform.TransformFinalBlock%2A> gera uma <xref:System.Security.Cryptography.CryptographicException> ou produz dados corrompidos.|O impacto deve ser mínimo, pois esse é o comportamento esperado.<br /><br /> Os aplicativos que dependem do comportamento anterior podem optar por não usá-lo adicionando a seguinte definição de configuração à seção [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:<br /><br /> `<runtime>    <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/> </runtime>`<br /><br /> Além disso, os aplicativos direcionados a uma versão anterior do .NET Framework, mas em execução em uma versão do .NET Framework começando com o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], podem aceitá-lo adicionando a seguinte definição de configuração à seção [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:<br /><br /> `<runtime>    <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/> </runtime>`|Secundário|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Suporte à segurança de transporte do WCF para certificados armazenados usando CNG|Começando com os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a segurança de transporte do WCF dá suporte a certificados armazenados usando a biblioteca de criptografia do Windows (CNG). Esse suporte é limitado a certificados com uma chave pública que tenha um expoente não superior a 32 bits de comprimento. Quando um aplicativo é direcionado ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], esse recurso é ativado por padrão.<br /><br /> Em versões anteriores do .NET Framework, a tentativa de usar os certificados X509 com um provedor de armazenamento de chaves CSG gera uma exceção.|Os aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões anteriores, mas que são executados no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], podem habilitar o suporte aos certificados CNG adicionando a seguinte linha à seção runtime do arquivo app.config ou web.config.<br /><br /> `<AppContextSwitchOverrides     value="Switch.System.ServiceModel.DisableCngCertificates=false" />`<br /><br /> Isso também pode ser feito de modo programático com o seguinte código:<br /><br /> `private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate"; AppContext.SetSwitch(disableCngCertificates, false);`<br /><br /> `Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates" AppContext.SetSwitch(disableCngCertificates, False)`<br /><br /> Observe que, por causa dessa alteração, qualquer código de tratamento de exceção que dependa da tentativa de iniciar a comunicação segura com um certificado CNG para falhar não será mais executado.|Secundário|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Forms  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>, `System.ComponentModel.EventDescriptor.Equals` e `System.ComponentModel.PropertyDescriptor.Equals`|A partir dos aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a implementação do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A> da classe base foi alterada.|Como o teste de igualdade agora gera o resultado esperado, essa alteração deve ter pouco efeito.<br /><br /> No entanto, os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] que dependem do comportamento anterior podem recusar essa alteração. Da mesma forma, os aplicativos direcionados a versões anteriores do .NET Framework, mas que são executados no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], podem aceitar essa alteração. Para saber mais, confira [Mitigation: MemberDescriptor.Equals](~/docs/framework/migration-guide/mitigation-memberdescriptor-equals.md) (Mitigação: MemberDescriptor.Equals).|Edge|  
  
## <a name="see-also"></a>Consulte também  
 [Compatibilidade de aplicativos na versão 4.6.2](~/docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
