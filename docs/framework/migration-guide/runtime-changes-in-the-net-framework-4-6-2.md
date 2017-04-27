---
title: "Alterações de tempo de execução no .NET Framework 4.6.2 | Microsoft Docs"
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
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6.2
- application compatibility
ms.assetid: 23bf3a87-6fa1-4b5e-b92c-a39867a06e7f
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: da809955776b5a5cd3776898ecc4c97db74ceb0e
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-462"></a>Alterações de tempo de execução no .NET Framework 4.6.2
Em casos raros, as alterações de tempo de execução podem afetar aplicativos existentes direcionados a versões anteriores do .NET Framework, mas que são executados em uma versão posterior do tempo de execução do .NET Framework. Elas também incluem diferenças no comportamento entre aplicativos que são executados em diferentes ambientes de tempo de execução do .NET Framework. O [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] inclui alterações nas seguintes áreas:  
  
-   [Core](#Core)  
  
-   [ASP.NET](#ASP)

-   [Dados](#Data)  
  
-   [WCF (Windows Communication Foundation)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [Assinatura e validação de XML](#XML)  
  
<a name="Core"></a>   
## <a name="core"></a>Núcleo  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName><br /><br /> <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory%2A?displayProperty=fullName>|As categorias de caracteres no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] são baseadas em Unicode versão 8.0. As versões de 4.5 a 4.6.1 do .NET Framework classificavam os caracteres Unicode com base no Unicode versão 6.3.<br /><br /> A comparação e a classificação de caracteres não são afetadas por essa alteração. Para saber mais, confira a seção "Cadeias de caracteres e o padrão Unicode" no tópico da classe <xref:System.String>.|As categorias de caracteres no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] podem não corresponder as de versões anteriores do .NET Framework. Essa alteração afeta basicamente sílabas cheroqui, bem como os símbolos vocálicos e as marcas de tom Tai Lue.<br /><br /> Para resolver esse problema, você deve examinar o código e remover ou alterar a lógica que depende de categorias de caractere Unicode embutido em código.|Secundário|  
|<xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.RSACng.ImportParameters%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A?displayProperty=fullName>, <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=fullName>|A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], esses métodos são capazes de acessar as chaves com tamanhos não padrão para certificados RSA. No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões anteriores, tentar acessar essas chaves gerava uma <xref:System.Security.Cryptography.CryptographicException>.|Se alguma lógica de tratamento de exceção depender de uma <xref:System.Security.Cryptography.CryptographicException> quando tamanhos de chave não padrão forem usados, ela deverá ser removida.|Edge|  
|<xref:System.Security.Cryptography.RSACng.VerifyHash%2A?displayProperty=fullName>|A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], esse método retornará `false` se a assinatura em si estiver incorretamente formatada. Agora ele retorna `false` para qualquer falha de verificação.<br /><br /> No [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e 4.6.1, o método vai gerar <xref:System.Security.Cryptography.CryptographicException> se a assinatura em si estiver incorretamente formatada.|Qualquer código cuja execução dependa da <xref:System.Security.Cryptography.CryptographicException> deverá ser executado se a validação falhar e o método retornar `false`.|Secundário|  
  
## <a name="a-nameasp--aspnet"></a><a name="ASP" /> ASP.NET

|Recurso|Alteração|Impacto|Escopo| 
|-------------|------------|------------|-----------|  
| <xref:System.Web.HttpRuntime.AppDomainApopPath%2A> | No .NET Framework 4.6.2, o tempo de execução gera uma <xref:System.NullReferenceException> ao recuperar um valor de <xref:System.Web.HttpRuntime.AppDomainAppPath%2A> que inclui caracteres nulo. No .NET Framework 4.6.1 e nas versões anteriores, ele lança uma <xref:System.ArgumentNullException>.  | Você pode fazer o seguinte para responder a essa alteração: <br/> - Tratar a <xref:System.NullReferenceException> se o aplicativo estiver em execução no .NET Framework 4.6.2. <br /> - Atualizar para o .NET Framework 4.7, que restaura o comportamento anterior e lança uma <xref:System.ArgumentNullException>. | Edge |

<a name="Data"></a>   
## <a name="data"></a>Dados  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Período de bloqueio do pool de conexões para bancos de dados SQL|Para solicitações de abertura de conexão com bancos de dados SQL conhecidos, o período de bloqueio do pool de conexões foi removido.|As tentativas de repetir as solicitações de abertura de conexão ocorrerão quase que imediatamente após os erros de conexão transitórios. Para saber mais, confira [Mitigation: Pool Blocking Period](~/docs/framework/migration-guide/mitigation-pool-blocking-period.md) (Mitigação: período de bloqueio de pool).|Secundário|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName> <br /> <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName>|Ao usar NetTcp com segurança de transporte e um tipo de credencial de certificado, o SSL 3 não é mais um protocolo padrão usado para negociar uma conexão segura.|Na maioria dos casos, não deve haver impacto nos aplicativos existentes, pois o TLS 1.0 sempre esteve incluído na lista de protocolos para NetTcp. Todos os clientes existentes devem ser capazes de negociar uma conexão usando, no mínimo, o TLS 1.0.<br /><br /> Se o Ssl3 for exigido, você poderá usar um dos seguintes mecanismos de configuração para adicioná-lo à lista de protocolos negociados:<br /><br /> -  A propriedade <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=fullName><br />-  A propriedade <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName><br />-  A seção [\<transport>](~/docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md) de [\<netTcpBinding>](~/docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)<br />-  A seção [\<sslStreamSecurity>](~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) de [\<customBinding>](~/docs/framework/configure-apps/file-schema/wcf/custombinding.md)|Edge|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|A propriedade `IsEnabled` do pai de um controle <xref:System.Windows.Controls.TextBlock>|A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], alterar a propriedade `IsEnabled` do pai de um controle <xref:System.Windows.Controls.TextBlock> afeta todos os controles filho (como hiperlinks e botões) do controle <xref:System.Windows.Controls.TextBlock>.<br /><br /> No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões anteriores do .NET Framework, os controles dentro de um <xref:System.Windows.Controls.TextBlock> nem sempre refletiam o estado da propriedade `IsEnabled` do pai <xref:System.Windows.Controls.TextBlock>.|Essa alteração está em conformidade com o comportamento esperado para controles dentro de um controle <xref:System.Windows.Controls.TextBlock>.|Secundário|  
|Rolagem horizontal, virtualização e <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName>|O comportamento da operação de rolagem para um <xref:System.Windows.Controls.ItemsControl> que faz sua própria virtualização na direção ortogonal para a principal direção de rolagem foi alterado.|A alteração proporciona uma experiência mais previsível e intuitiva para o usuário final, mas ela pode afetar qualquer aplicativo que dependa do valor exato de <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> após uma rolagem horizontal. Para saber mais, confira [Atenuação: Rolagem Horizontal e virtualização](~/docs/framework/migration-guide/mitigation-horizontal-scrolling-and-virtualization.md).|Secundário|  
|Verificador ortográfico do WPF (classe <xref:System.Windows.Controls.SpellCheck?displayProperty=fullName>)|Três problemas apontados na verificação ortográfica do WPF quando executada no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] foram resolvidos no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:<br /><br /> - No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], o verificador ortográfico, às vezes, gera uma <xref:System.Runtime.InteropServices.COMException> ao invocar os métodos [ISpellChecker](https://msdn.microsoft.com/library/windows/desktop/hh869767\(v=vs.85\).aspx) ou [ISpellCheckerFactory](https://msdn.microsoft.com/library/windows/desktop/hh869770\(v=vs.85\).aspx). No [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], essas exceções foram eliminadas.<br />- No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], o verificador ortográfico identifica incorretamente os erros ortográficos em palavras compostas, como "Hausnummer", em alemão. No [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], o verificador ortográfico trata corretamente as palavras compostas.<br />- No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], o verificador ortográfico gera uma <xref:System.UnauthorizedAccessException> quando um aplicativo é iniciado usando "executar como usuário diferente". No [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], não há suporte para esse cenário e o verificador ortográfico é silenciosamente desabilitado.|Essas alterações melhoram a robustez do verificador ortográfico.  Elas não devem afetar negativamente um aplicativo, a menos que o código do aplicativo dependa de uma exceção que está sendo emitida.|Edge|  
| Método [DataGridCellsPanel.BringIndexIntoView](xref:System.Windows.Controls.DataGridCellsPanel.BringIndexInfoView(System.Int32)) | No .NET Framework 4.6.2, o método **BringIndexIntoView** será executado assincronamente quando a virtualização de coluna estiver habilitada, mas as larguras das colunas não tiverem sido determinadas. No entanto, se as colunas forem removidas antes que a operação assíncrona seja concluída, uma [ArgumentOutOfRangeException](xref:System.ArgumentOutOfRangeException) poderá ocorrer.<br/></br>A partir do .NET Framework 4.7, a exceção não é mais gerada neste cenário. | Você pode executar qualquer um dos seguintes procedimentos para evitar que a exceção ocorra: <br/> - Atualizar para o .NET Framework 4.7. <br/> - Instalar o patch de serviço mais recente para o .NET Framework 4.6.2. <br/> - Evitar remover colunas até que a resposta assíncrona ao método [DataGrid.ScrollIntoView](xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)) seja concluída. | Edge | 
  
<a name="XML"></a>   
## <a name="signed-xml-verification-requirements"></a>Requisitos de verificação de XML assinado  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> e <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName>|O carregamento de recurso externo é desabilitado e destinos de id ambíguos são considerados inválidos.|Uma exceção é gerada em vários casos, incluindo:<br /><br /> - Identificar um elemento por um atributo de id e definir um segundo elemento com o mesmo identificador.<br />- Definir um identificador que não é um valor `NCName` legal.<br />- Fazer referência a URIs externos.<br /><br /> <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A?displayProperty=fullName> sempre retorna `false` para documentos:<br /><br /> - Que usam a transformação de referência XPath.<br />- Que usam a transformação de referência XSLT.<br /><br /> Os desenvolvedores devem analisar o uso de <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=fullName> e <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, bem como tipos derivados de <xref:System.Security.Cryptography.Xml.Transform?displayProperty=fullName>, uma vez que o destinatário do documento pode não estar apto a processá-lo.<br /><br /> Para saber mais, confira [Depois de aplicar a atualização de segurança 3141780, os aplicativos do .NET Framework encontram erros de exceção ou falhas inesperadas durante o processamento de arquivos que contêm SignedXml](https://support.microsoft.com/en-us/kb/3148821).|Secundário|  
  
## <a name="see-also"></a>Consulte também  
 [Compatibilidade de aplicativos na versão 4.6.2](~/docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
