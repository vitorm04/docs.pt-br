---
title: "Alterações no tempo de execução no .NET Framework 4.5.2 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94ac01ea-8b12-44d2-b12b-5220a5d14d87
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 247fbf574f13985fc941f252c0a6e7268194c079
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-452"></a>Alterações no tempo de execução do .NET Framework 4.5.2
Em casos raros, as alterações em tempo de execução podem afetar aplicativos existentes destinados a versões anteriores do .NET Framework mas que são executados em tempo de execução do .NET Framework 4.5.2. Entre eles estão alterações feitas nas seguintes áreas:  
  
-   [ASP.NET](#ASP_NET)  
  
-   [Entity Framework](#EF)  
  
<a name="ASP_NET"></a>   
## <a name="aspnet-runtime-changes"></a>Alterações em tempo de execução do ASP.NET  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Atributo `enableViewStateMac` dos elementos da página [ ](http://msdn.microsoft.com/en-us/4123bb66-3fe4-4d62-b70e-33758656b458)|O ASP.NET não permite mais que os desenvolvedores especifiquem:<br /><br /> `<pages enableViewStateMac="false" />`<br /><br /> ou:<br /><br /> `<@Page EnableViewStateMac="false" %>`|O MAC (Message Authentication Code) de estado da exibição agora é obrigatório em todas as solicitações com estado de exibição embutido. Apenas aplicativos que definiram explicitamente a propriedade <xref:System.Web.UI.Page.EnableViewStateMac%2A> como `false` são afetados.<br /><br /> Para saber mais, veja [Resolvendo erros do código de autenticação da mensagem (MAC) no estado de exibição](http://support.microsoft.com/kb/2915218).|Principal|  
  
<a name="EF"></a>   
## <a name="entity-framework-runtime-changes"></a>Alterações de tempo de execução do Entity Framework  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Relacionamento em um QueryView|O Entity Framework já não lança uma exceção <xref:System.StackOverflowException> quando um aplicativo executa uma consulta que envolve QueryView com uma propriedade de navegação de 0.1 que tenta incluir as entidades relacionadas como parte da consulta (por exemplo, chamando `.Include(e=>e.RelatedNavProp)`.|Essa alteração afeta apenas o código que usa relacionamentos de QueryViews com 1-0..1 ao executar consultas que chamam `.Include`. Isso melhora a confiabilidade e deve ser transparente para quase todos os aplicativos. No entanto, se causa um comportamento inesperado, é possível desabilitá-lo adicionando a seguinte entrada à seção `<appSettings>` do arquivo de configuração do aplicativo:<br /><br /> `<add key="EntityFramework_SimplifyUserSpecifiedViews"  value="false" />`|Edge|  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-2.md)   
 [Compatibilidade de aplicativos no 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilidade de aplicativos no 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)
