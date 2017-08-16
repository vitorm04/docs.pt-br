---
title: "Mitigação: MemberDescriptor.Equals"
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
ms.assetid: cf3735f0-0dd4-4bef-b4b0-575264e10f39
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4989d3c2611b500063158955f102931902e1ab32
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-memberdescriptorequals"></a>Mitigação: MemberDescriptor.Equals
Começando com os aplicativos que direcionam o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a implementação do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> foi alterada. Como os métodos `System.ComponentModel.EventDescriptor.Equals` e `System.ComponentModel.PropertyDescriptor.Equals` herdam a implementação da classe base, a alteração também afeta esses métodos.  
  
 Em aplicativos que direcionam versões do .NET Framework antes do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], uma parte do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> de igualdade comparou incorretamente a propriedade <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> de um objeto com a propriedade <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> do outro. Começando com aplicativos que direcionam o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], o método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> compara a propriedade <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> dos dois objetos.  
  
## <a name="impact"></a>Impacto  
 Essa alteração implementa corretamente o teste de igualdade para objetos <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> e deve ter um impacto mínimo.  
  
## <a name="mitigation"></a>Redução  
 Duas soluções alternativas estarão disponíveis se o seu aplicativo direcionar o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou uma versão posterior do .NET Framework e ela depender do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> que às vezes retornará `false` quando os descritores de membro forem equivalentes:  
  
-   Você pode recusar essa alteração sem modificar seu código-fonte adicionando o seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
    ```  
  
-   É possível modificar seu código-fonte para restaurar o comportamento anterior comparando manualmente as propriedades <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> e <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> após chamar o método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>, como o fragmento de código a seguir faz.  
  
    ```csharp  
    if (memberDescriptor1.Equals(memberDescriptor2) &   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)) {  
          // Code to execute if true.  
    }  
    else {  
          // Code to execute if false.     
    }  
    ```  
  
    ```  
    If memberDescriptor1.Equals(memberDescriptor2) And   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)  
          // Code to execute if True.  
    Else  
          // Code to execute if False.     
    End If  
    ```  
  
 Para aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e em versões anteriores, você pode habilitar essa alteração adicionando o seguinte valor ao seu arquivo app.config:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)   
 [Compatibilidade de aplicativos no 4.6.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)

