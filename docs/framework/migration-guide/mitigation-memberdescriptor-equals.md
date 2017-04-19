---
title: "Mitigação: MemberDescriptor.Equals | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 409f06f4dfbe7be50dd2c487e49d3d4d8a477539
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-memberdescriptorequals"></a>Mitigação: MemberDescriptor.Equals
Começando com os aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a implementação do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> mudou. Como os métodos `System.ComponentModel.EventDescriptor.Equals` e `System.ComponentModel.PropertyDescriptor.Equals` herdam a implementação da classe base, a alteração também afeta esses métodos.  
  
 Em aplicativos direcionados a versões do .NET Framework anteriores ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], uma parte do teste de igualdade do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> comparou incorretamente a propriedade <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> de um objeto com a propriedade <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> de outro. A partir dos aplicativos direcionados ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], o método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> compara a propriedade <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> dos dois objetos.  
  
## <a name="impact"></a>Impacto  
 Essa alteração implementa corretamente o teste de igualdade para objetos <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> e deve ter um impacto mínimo.  
  
## <a name="mitigation"></a>Redução  
 Há duas soluções alternativas disponíveis se o seu aplicativo for direcionado ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou a uma versão posterior do .NET Framework e se depender do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> retornar, às vezes, `false` quando os descritores de membro forem equivalentes:  
  
-   Você pode recusar essa alteração sem modificar seu código-fonte adicionando o seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:  
  
    ```xml  
  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
  
    ```  
  
-   Modifique seu código-fonte para restaurar o comportamento anterior comparando manualmente as propriedades <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> e <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> depois de chamar o método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>, como faz o seguinte fragmento de código.  
  
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
    \<AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)   
 [Compatibilidade de aplicativos no 4.6.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
