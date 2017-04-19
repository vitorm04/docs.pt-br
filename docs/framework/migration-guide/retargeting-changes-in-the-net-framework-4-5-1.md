---
title: "Alterações de redirecionamento no .NET Framework 4.5.1 | Microsoft Docs"
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
- application compatibility
- retargeting changes
- .NET Framework 4.5.1
- retargeting changes, .NET Framework 4.5.1
- retargeting changes, .NET Framework
ms.assetid: 8087326d-77e9-4804-ba33-ff1bb1bec2b8
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0c497561254c0f97f22ac05c7d44224b30ef74d0
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-451"></a>Alterações no redirecionamento no .NET Framework 4.5.1
Em casos raros, alterações de redirecionamento podem afetar aplicativos recompilados para segmentar o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]. Eles não afetam binários que segmentem uma versão anterior do .NET Framework, mas são executados na versão 4.5.1. O [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] inclui alterações de redirecionamento nas seguintes áreas:  
  
-   [Core](#Core)  
  
-   [ADO.NET](#ADO)  
  
-   [MSBuild](#MSBuild)  
  
 A coluna Escopo nas tabelas a seguir especifica o significado de cada alteração:  
  
-   Principal. Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código. Observe que nenhuma das alterações de redirecionamento entra nessa categoria.  
  
-   Secundário. Uma alteração que afeta um pequeno número de aplicativos ou que exige a modificação secundária do código.  
  
-   Borda. Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.  
  
-   Transparente. Uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.  
  
<a name="Core"></a>   
## <a name="core-retargeting-changes"></a>Alterações de redirecionamento básico  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Atributo <xref:System.ObsoleteAttribute?displayProperty=fullName>|Quando você cria uma biblioteca de Metadados do Windows (arquivo .winmd), o atributo <xref:System.ObsoleteAttribute> é exportado como <xref:System.ObsoleteAttribute> e [Windows.Foundation.DeprecatedAttribute](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.deprecatedattribute.aspx).|A recompilação do código-fonte existente que usa o atributo <xref:System.ObsoleteAttribute> pode gerar avisos durante o consumo desse código no C++/CX ou JavaScript.<br /><br /> Não é aconselhável a aplicação de <xref:System.ObsoleteAttribute> e [Windows.Foundation.DeprecatedAttribute](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.deprecatedattribute.aspx) para codificar em assemblies gerenciados; isso pode resultar em avisos de compilação.<br /><br /> Para saber mais, confira o tópico de referência <xref:System.ObsoleteAttribute>.|Edge|  
  
<a name="ADO"></a>   
## <a name="adonet-retargeting-changes"></a>Alterações de redirecionamento do ADO.NET  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Classe <xref:System.Data.Common.DbParameter?displayProperty=fullName>|<xref:System.Data.Common.DbParameter.Precision%2A?displayProperty=fullName> e <xref:System.Data.Common.DbParameter.Scale%2A?displayProperty=fullName> são implementadas como propriedades virtuais públicas. Elas substituem as implementações explícitas da interface, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision%2A?displayProperty=fullName> e <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale%2A?displayProperty=fullName>.|A alteração afeta apenas os desenvolvedores que compilam um provedor de banco de dados do ADO.NET.|Borda|  
  
<a name="MSBuild"></a>   
## <a name="msbuild-retargeting-changes"></a>Alterações de redirecionamento do MSBuild  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Tarefa `ResolveAssemblyReference`|A tarefa emite um aviso, MSB3270, que indica que uma referência ou qualquer uma de suas dependências não corresponde à arquitetura do aplicativo. Por exemplo, isso ocorrerá se um aplicativo que tenha sido compilado com a opção `anycpu` incluir uma referência x86. Esse cenário pode resultar em uma falha do aplicativo no tempo de execução (nesse caso, se o aplicativo for implantado como um processo x64).|Há duas áreas de impacto:<br /><br /> -   A recompilação gera avisos que não foram exibidos quando o aplicativo foi compilado com uma versão anterior do MSBuild. Entretanto, como o aviso identifica uma possível fonte de falha no tempo de execução, ele deve ser investigado e resolvido.<br />-   Se os avisos forem tratados como erros, o aplicativo não será compilado.|Secundário|  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)   
 [Compatibilidade de aplicativos no 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilidade de aplicativos no 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)
