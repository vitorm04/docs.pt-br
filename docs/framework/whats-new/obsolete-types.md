---
title: Tipos obsoletos no .NET Framework | Microsoft Docs
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
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
caps.latest.revision: 41
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 01c66e2c291766ba00376261740906934f065855
ms.openlocfilehash: b7040d4c82c9434b2d24a579a93602660479ec59
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# Tipos obsoletos no .NET Framework
<a id="obsolete-types-in-the-net-framework" class="xliff"></a>
<a name="introduction"></a>As tabelas deste artigo listam os tipos que estão obsoletos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], organizados por assembly. Use os links a seguir para ver uma lista dos tipos obsoletos e das alternativas recomendadas em cada assembly. Como esses tipos são obsoletos, todos seus membros também estão obsoletos. Para obter uma lista de membros obsoletos adicionais na biblioteca de classes .NET Framework, confira [Membros obsoletos](../../../docs/framework/whats-new/obsolete-members.md).  
  
-   [Tipos obsoletos em assemblies de sistema](#obsolete_types_in_system_assemblies)  
  
    -   [mscorlib.dll](#mscorlib)  
  
    -   [System.Core.dll](#Core)  
  
    -   [System.Data.dll](#data)  
  
    -   [System.Data.OracleClient.dll](#oracleclient)  
  
    -   [System.Design.dll](#design)  
  
    -   [System.dll](#system)  
  
    -   [System.EnterpriseServices.dll](#enterpriseservices)  
  
    -   [System.Net.dll](#net)  
  
    -   [System.ServiceModel.dll](#servicemodel)  
  
    -   [System.Web.dll](#web)  
  
    -   [System.Web.Mobile.dll](#mobile)  
  
    -   [System.Workflow.Activities.dll](#workflow_activities)  
  
    -   [System.Workflow.ComponentModel.dll](#workflow_componentmodel)  
  
    -   [System.Workflow.Runtime.dll](#workflow_runtime)  
  
    -   [System.WorkflowServices.dll](#workflowservices)  
  
    -   [System.Xaml.dll](#xaml)  
  
    -   [System.Xml.dll](#xml)  
  
    -   [WindowsBase.dll](#WindowsBase)  
  
-   [Tipos obsoletos em assemblies Microsoft](#obsolete_types_in_microsoft_assemblies)  
  
    -   [IEHost.dll e IEExec.exe](#IEHost)  
  
    -   [Microsoft.Build.Engine.dll](#Engine)  
  
    -   [Microsoft.JScript.dll](#jscript)  
  
    -   [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)  
  
    -   [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)  
  
    -   [Microsoft.VisualC.dll](#visualc)  
  
<a name="obsolete_types_in_system_assemblies"></a>   
## Tipos obsoletos em assemblies de sistema
<a id="obsolete-types-in-system-assemblies" class="xliff"></a>  
 As tabelas a seguir listam os tipos que foram declarados obsoletos em assemblies de sistema. Esses assemblies são usados no desenvolvimento de aplicativos de uso\-geral direcionados ao .NET Framework.  
  
<a name="mscorlib"></a>   
### Assembly: mscorlib.dll
<a id="assembly-mscorlibdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.ExecutionEngineException?displayProperty=fullName>|Esse tipo indicava um erro fatal não especificado no tempo de execução. Como o tempo de execução não aciona mais essa exceção, esse tipo está obsoleto.|  
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=fullName>|Use <xref:System.StringComparer?displayProperty=fullName> em seu lugar.|  
|<xref:System.Collections.IHashCodeProvider?displayProperty=fullName>|Use <xref:System.Collections.IEqualityComparer?displayProperty=fullName> em seu lugar.|  
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=fullName>|A classe <xref:System.Configuration.Assemblies.AssemblyHash> foi substituída.|  
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5. Em vez disso, use a classe <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=fullName> no namespace System.Runtime.CompilerServices.|  
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=fullName>|Uma API alternativa está disponível: emita o atributo personalizado <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=fullName>|Esse atributo foi substituído e será removido em uma versão futura.|  
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=fullName>|O <xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=fullName> foi substituído.|  
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=fullName>|Esse atributo foi substituído. Domínios de aplicativo não respeitam mais limites do contexto de ativação em chamadas IDispatch.|  
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=fullName> em seu lugar.|  
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=fullName>|Use <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=fullName> em seu lugar.|  
|<xref:System.Security.SecurityCriticalScope?displayProperty=fullName>|<xref:System.Security.SecurityCriticalScope> só é usado na compatibilidade de transparência do .NET 2.0.|  
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=fullName>|<xref:System.Security.SecurityTreatAsSafeAttribute> só é usado na compatibilidade de transparência do .NET 2.0. Use <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=fullName> em seu lugar.|  
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=fullName>|Esse tipo é obsoleto e será removido em uma versão futura do .NET Framework.|  
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=fullName>|A segurança declarativa no nível do assembly é obsoleta e não é mais imposta pelo CLR por padrão.|  
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=fullName>|Esse tipo é obsoleto e será removido em uma versão futura do .NET Framework.|  
  
 [Voltar ao início](#introduction)  
  
<a name="Core"></a>   
### Assembly: System.Core.dll
<a id="assembly-systemcoredll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=fullName>|O uso desse tipo gera um erro do compilador.<br /><br /> Não use esse tipo.|  
  
 [Voltar ao início](#introduction)  
  
<a name="data"></a>   
### Assembly: System.Data.dll
<a id="assembly-systemdatadll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=fullName>|<xref:System.Data.DataSysDescriptionAttribute> foi preterido.|  
|<xref:System.Data.PropertyAttributes?displayProperty=fullName>|<xref:System.Data.PropertyAttributes> foi preterido.|  
|<xref:System.Data.TypedDataSetGenerator?displayProperty=fullName>|A classe <xref:System.Data.TypedDataSetGenerator> será removida em uma versão futura. Use <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=fullName> em System.Design.dll.|  
|<xref:System.Xml.XmlDataDocument?displayProperty=fullName>|A classe <xref:System.Xml.XmlDataDocument> será removida em uma versão futura.|  
  
 [Voltar ao início](#introduction)  
  
<a name="oracleclient"></a>   
### Assembly: System.Data.OracleClient.dll
<a id="assembly-systemdataoracleclientdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleClientFactory> foi preterido.|  
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleCommand> foi preterido.|  
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleCommandBuilder> foi preterido.|  
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleConnection> foi preterido.|  
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> foi preterido.|  
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleDataAdapter> foi preterido.|  
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>|<xref:System.Data.OracleClient.OraclePermission> foi preterido.|  
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName> foi preterido.|  
  
 [Voltar ao início](#introduction)  
  
<a name="design"></a>   
### Assembly: System.Design.dll
<a id="assembly-systemdesigndll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=fullName>|Essa classe foi substituída. Use <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=fullName> em seu lugar.|  
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=fullName>|O uso desse tipo não é recomendado porque a edição de DataBindings é iniciada por meio de <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=fullName> em vez da grade de propriedade.|  
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=fullName>|O uso desse tipo não é recomendado porque a edição de DataBindings é iniciada por meio de <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=fullName> em vez da grade de propriedade.|  
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=fullName>|A alternativa recomendada é <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=fullName> e <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=fullName>|A alternativa recomendada é <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=fullName> e <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=fullName>|O uso de esse tipo não é recomendado porque a edição do modelo é identificada em <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName>. Para dar suporte à edição do modelo, exponha os dados do modelo na propriedade <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> e chame <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=fullName>|A alternativa recomendada é <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=fullName>. O <xref:System.Web.UI.Design.WebFormsReferenceManager> contém funcionalidade adicional e possibilita mais extensibilidade. Para obter o <xref:System.Web.UI.Design.WebFormsReferenceManager>, use a propriedade `RootDesigner.ReferenceManager` do seu <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=fullName>|A alternativa recomendada é <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=fullName>. O <xref:System.Web.UI.Design.WebFormsRootDesigner> contém funcionalidade adicional e possibilita mais extensibilidade. Para obter o <xref:System.Web.UI.Design.WebFormsRootDesigner>, use a propriedade <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> do seu <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=fullName>|O uso de esse tipo não é recomendado porque a edição do modelo é identificada em <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName>. Para dar suporte à edição do modelo, exponha os dados do modelo na propriedade <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> e chame <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=fullName>|A alternativa recomendada é <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=fullName> porque ela usa um <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=fullName> para editar o conteúdo. Regiões de designer possibilitam um melhor controle do conteúdo que está sendo editado.|  
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=fullName>|O uso de esse tipo não é recomendado porque a edição do modelo é identificada em <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName>. Para dar suporte à edição do modelo, exponha os dados do modelo na propriedade <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> e chame <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=fullName>|O uso de esse tipo não é recomendado porque a edição do modelo é identificada em <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName>. Para dar suporte à edição do modelo, exponha os dados do modelo na propriedade <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> e chame <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=fullName>|O uso desse tipo não é recomendado porque a caixa de diálogo AutoFormat é iniciada pelo host do designer. A lista de AutoFormats disponíveis está exposta na <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> propriedade <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=fullName>.|  
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=fullName>|A alternativa recomendada é <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=fullName> porque ela usa um <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=fullName> para editar o conteúdo. Regiões de designer possibilitam um melhor controle do conteúdo que está sendo editado.|  
  
 [Voltar ao início](#introduction)  
  
<a name="system"></a>   
### Assembly: System.dll
<a id="assembly-systemdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=fullName>|Essa interface foi substituída. Adicione um <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=fullName> ao tipo de identificador <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=fullName> em vez disso.|  
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=fullName>|Use <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=fullName> em seu lugar para trabalhar com o novo modelo de configurações.|  
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=fullName>|Esse atributo foi substituído. Use <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=fullName> em seu lugar. Por exemplo, para especificar um designer raiz para CodeDom, use `DesignerSerializerAttribute\(...,typeof\(TypeCodeDomSerializer\)\)`.|  
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=fullName>|Essa classe foi substituída.|  
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=fullName>|Essa classe foi substituída. Use os contadores de desempenho por meio da classe <xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName> em seu lugar.|  
|<xref:System.Net.GlobalProxySelection?displayProperty=fullName>|Essa classe foi substituída. Use <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=fullName> em seu lugar para acessar e definir o proxy padrão global. Use 'null' em lugar de <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=fullName>.|  
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
  
 [Voltar ao início](#introduction)  
  
<a name="enterpriseservices"></a>   
### Assembly: System.EnterpriseServices.dll
<a id="assembly-systementerpriseservicesdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=fullName>|A classe <xref:System.EnterpriseServices.RegistrationHelperTx> foi substituída.|  
  
 [Voltar ao início](#introduction)  
  
<a name="net"></a>   
### Assembly: System.Net.dll
<a id="assembly-systemnetdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Net.INetworkProgress?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Net.UiSynchronizationContext?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
  
 [Voltar ao início](#introduction)  
  
<a name="servicemodel"></a>   
### Assembly: System.ServiceModel.dll
<a id="assembly-systemservicemodeldll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O recurso de canal par está obsoleto e será removido no futuro.|  
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Esse tipo está obsoleto. Para habilitar HTTP <xref:System.Net.CookieContainer>, use a propriedade `AllowCookies` na associação HTTP ou no <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.|  
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O recurso de canal par está obsoleto e será removido no futuro.|  
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O recurso de canal par está obsoleto e será removido no futuro.|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O recurso de canal par está obsoleto e será removido no futuro.|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O recurso de canal par está obsoleto e será removido no futuro.|  
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O recurso de canal par está obsoleto e será removido no futuro.|  
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O recurso de canal par está obsoleto e será removido no futuro.|  
  
 [Voltar ao início](#introduction)  
  
<a name="web"></a>   
### Assembly: System.Web.dll
<a id="assembly-systemwebdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=fullName>|Esse tipo está obsoleto. O produto de autenticação Passport não é mais compatível e foi substituído pela [Conta da Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Mail.MailAttachment?displayProperty=fullName>|A alternativa recomendada é <xref:System.Net.Mail.Attachment?displayProperty=fullName>.|  
|<xref:System.Web.Mail.MailEncoding?displayProperty=fullName>|A alternativa recomendada é <xref:System.Net.Mime.TransferEncoding?displayProperty=fullName>.|  
|<xref:System.Web.Mail.MailFormat?displayProperty=fullName>|A alternativa recomendada é <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=fullName>.|  
|<xref:System.Web.Mail.MailMessage?displayProperty=fullName>|A alternativa recomendada é <xref:System.Net.Mail.MailMessage?displayProperty=fullName>.|  
|<xref:System.Web.Mail.MailPriority?displayProperty=fullName>|A alternativa recomendada é <xref:System.Net.Mail.MailPriority?displayProperty=fullName>.|  
|<xref:System.Web.Mail.SmtpMail?displayProperty=fullName>|A alternativa recomendada é <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>.|  
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=fullName>|Esse tipo está obsoleto. O produto de autenticação Passport não é mais compatível e foi substituído pela [Conta da Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=fullName>|Esse tipo está obsoleto. O produto de autenticação Passport não é mais compatível e foi substituído pela [Conta da Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=fullName>|Esse tipo está obsoleto. O produto de autenticação Passport não é mais compatível e foi substituído pela [Conta da Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportIdentity?displayProperty=fullName>|Esse tipo está obsoleto. O produto de autenticação Passport não é mais compatível e foi substituído pela [Conta da Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportPrincipal?displayProperty=fullName>|Esse tipo está obsoleto. O produto de autenticação Passport não é mais compatível e foi substituído pela [Conta da Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.UI.ObjectConverter?displayProperty=fullName>|A alternativa recomendada é <xref:System.Convert?displayProperty=fullName> e <xref:System.String.Format%2A?displayProperty=fullName>.|  
  
 [Voltar ao início](#introduction)  
  
<a name="mobile"></a>   
### Assembly: System.Web.Mobile.dll
<a id="assembly-systemwebmobiledll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Web.Mobile.CookielessData?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Command?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Form?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Image?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Label?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Link?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.List?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Style?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=fullName>|O assembly System.Web.Mobile.dll foi substituído e não deve ser mais usado. Para saber mais sobre como desenvolver aplicativos móveis ASP.NET, confira [ASP.NET for Mobiles](http://go.microsoft.com/fwlink/?LinkId=157231) (ASP.NET para mobilidade).|  
  
 [Voltar ao início](#introduction)  
  
<a name="workflow_activities"></a>   
### Assembly: System.Workflow.Activities.dll
<a id="assembly-systemworkflowactivitiesdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|Todos os tipos no namespace <xref:System.Workflow.Activities?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
  
 [Voltar ao início](#introduction)  
  
<a name="workflow_componentmodel"></a>   
### Assembly: System.Workflow.ComponentModel.dll
<a id="assembly-systemworkflowcomponentmodeldll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|Todos os tipos no namespace <xref:System.Workflow.ComponentModel>, exceto <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=fullName> e <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|Todos os tipos no namespace <xref:System.Workflow.ComponentModel.Compiler>, exceto <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=fullName> e <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|Todos os tipos no namespace <xref:System.Workflow.ComponentModel.Design>, exceto <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
  
 [Voltar ao início](#introduction)  
  
<a name="workflow_runtime"></a>   
### Assembly: System.Workflow.Runtime.dll
<a id="assembly-systemworkflowruntimedll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------| 
|<xref:System.Activities.Statements.Interop>|Substituído primeiramente no .NET Framework 4.5.<br /><br />Os tipos Workflow Foundation 3.0 foram preteridos. Em vez disso, use os tipos do Workflow 4.0 de <xref:System.Activities>.\*.|  
|<xref:System.Activities.Tracking.InteropTrackingRecord>|Substituído primeiramente no .NET Framework 4.5.<br /><br />Os tipos Workflow Foundation 3.0 foram preteridos. Em vez disso, use os tipos do Workflow 4.0 de <xref:System.Activities>.\*.|   
|Todos os tipos no namespace <xref:System.Workflow.Runtime>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|Todos os tipos no namespace <xref:System.Workflow.Runtime.Configuration>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|Todos os tipos no namespace <xref:System.Workflow.Runtime.DebugEngine>, exceto <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|Todos os tipos no namespace <xref:System.Workflow.Runtime.Hosting>, exceto <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
|Todos os tipos no namespace <xref:System.Workflow.Runtime.Tracking>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos System.Workflow.\* foram preteridos. Em vez de isso, use os novos tipos de <xref:System.Activities>.\*.|  
  
 [Voltar ao início](#introduction)  
  
<a name="workflowservices"></a>   
### Assembly: System.WorkflowServices.dll
<a id="assembly-systemworkflowservicesdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|Todos os tipos no namespace <xref:System.Workflow.Activities?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> Os tipos WF 3 foram substituídos. Em vez de isso, use os novos tipos do WF 4 de <xref:System.Activities>.\*.|  
  
 [Voltar ao início](#introduction)  
  
<a name="xaml"></a>   
### Assembly: System.Xaml.dll
<a id="assembly-systemxamldll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=fullName>|Ele não é usado pelo analisador XAML. Observe <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=fullName>.|  
  
 [Voltar ao início](#introduction)  
  
<a name="xml"></a>   
### Assembly: System.Xml.dll
<a id="assembly-systemxmldll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=fullName>|Substituído primeiramente no .NET Framework 4.5.<br /><br /> O uso desse tipo gera um erro do compilador.<br /><br /> Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=fullName>|Use <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=fullName> na compilação e na validação do esquema.|  
|<xref:System.Xml.XmlValidatingReader?displayProperty=fullName>|Use um <xref:System.Xml.XmlReader?displayProperty=fullName> criado pelo método <xref:System.Xml.XmlReader.Create%2A?displayProperty=fullName> usando o <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> apropriado em seu lugar.|  
|<xref:System.Xml.XmlXapResolver?displayProperty=fullName>|O uso desse tipo gera um erro do compilador. Essa API dá suporte à infraestrutura do .NET Framework e não deve ser usada diretamente no código.|  
|<xref:System.Xml.Xsl.XslTransform?displayProperty=fullName>|Essa classe foi substituída. Use <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=fullName> em seu lugar.|  
  
 [Voltar ao início](#introduction)  
  
<a name="WindowsBase"></a>   
### Assembly: WindowsBase.dll
<a id="assembly-windowsbasedll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=fullName>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=fullName> foi preterido. Essa interface não é mais usada.|  
  
 [Voltar ao início](#introduction)  
  
<a name="obsolete_types_in_microsoft_assemblies"></a>   
## Tipos obsoletos em assemblies Microsoft
<a id="obsolete-types-in-microsoft-assemblies" class="xliff"></a>  
 As seções a seguir listam os tipos obsoletos em assemblies Microsoft. Esses assemblies são assemblies de finalidade especial, como assemblies que segmentam uma linguagem individual (por exemplo, Microsoft.JScript.dll ou Microsoft.VisualC.dll).  
  
<a name="IEHost"></a>   
### Assembly: IEHost.dll e IEExec.exe
<a id="assembly-iehostdll-and-ieexecexe" class="xliff"></a>  
 Os assemblies IEHost.dll e IEExec.exe foram removidos do .NET Framework. Todos os tipos e seus membros são obsoletos e não são compatíveis desde o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Esses assemblies foram usados para hospedar controles de Windows Forms e executar executáveis no Internet Explorer. Entre as alternativas recomendadas estão ClickOnce, aplicativos de navegador XAML (XBAP) e o Microsoft Silverlight.  
  
 [Voltar ao início](#introduction)  
  
<a name="Engine"></a>   
### Assembly: Microsoft.Build.Engine.dll
<a id="assembly-microsoftbuildenginedll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=fullName>|Essa classe foi substituída. Use <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=fullName> do assembly *Microsoft.Build* em seu lugar.|  
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=fullName>|Essa classe foi substituída. Use <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=fullName> do assembly *Microsoft.Build* em seu lugar.|  
  
 [Voltar ao início](#introduction)  
  
<a name="jscript"></a>   
### Assembly: Microsoft.JScript.dll
<a id="assembly-microsoftjscriptdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=fullName>|O uso desse tipo não é recomendado porque está sendo substituído no Visual Studio 2005; não haverá substituição desse recurso. Consulte a documentação de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> para obter ajuda adicional.|  
  
 [Voltar ao início](#introduction)  
  
<a name="VBCompat"></a>   
### Assembly: Microsoft.VisualBasic.Compatibility.dll
<a id="assembly-microsoftvisualbasiccompatibilitydll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
  
 [Voltar ao início](#introduction)  
  
<a name="VBCompatData"></a>   
### Assembly: Microsoft.VisualBasic.Compatibility.Data.dll
<a id="assembly-microsoftvisualbasiccompatibilitydatadll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=fullName>|Observe que [Microsoft.VisualBasic.Compatibility.VB6.\<member> está obsoleto e tem suporte apenas em processos de 32 bits](https://msdn.microsoft.com/library/ee839621.aspx).|  
  
 [Voltar ao início](#introduction)  
  
<a name="visualc"></a>   
### Assembly: Microsoft.VisualC.dll
<a id="assembly-microsoftvisualcdll" class="xliff"></a>  
  
|Tipo|Mensagem|  
|----------|-------------|  
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=fullName>|Microsoft.VisualC.dll é um assembly obsoleto e existe somente para compatibilidade com versões anteriores.|  
  
## Consulte também
<a id="see-also" class="xliff"></a>  
 [O que está obsoleto na Biblioteca de Classes](../../../docs/framework/whats-new/whats-obsolete.md)   
 [Membros obsoletos](../../../docs/framework/whats-new/obsolete-members.md)

