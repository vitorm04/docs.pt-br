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
# <a name="mitigation-memberdescriptorequals"></a><span data-ttu-id="22141-102">Mitigação: MemberDescriptor.Equals</span><span class="sxs-lookup"><span data-stu-id="22141-102">Mitigation: MemberDescriptor.Equals</span></span>
<span data-ttu-id="22141-103">Começando com os aplicativos que direcionam o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a implementação do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> foi alterada.</span><span class="sxs-lookup"><span data-stu-id="22141-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method has changed.</span></span> <span data-ttu-id="22141-104">Como os métodos `System.ComponentModel.EventDescriptor.Equals` e `System.ComponentModel.PropertyDescriptor.Equals` herdam a implementação da classe base, a alteração também afeta esses métodos.</span><span class="sxs-lookup"><span data-stu-id="22141-104">Because the `System.ComponentModel.EventDescriptor.Equals` and  `System.ComponentModel.PropertyDescriptor.Equals` methods inherit the base class implementation, the change also affects these methods.</span></span>  
  
 <span data-ttu-id="22141-105">Em aplicativos que direcionam versões do .NET Framework antes do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], uma parte do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> de igualdade comparou incorretamente a propriedade <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> de um objeto com a propriedade <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> do outro.</span><span class="sxs-lookup"><span data-stu-id="22141-105">In apps that target versions of the .NET Framework prior to [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a portion of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method's test for equality  incorrectly compared the <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> property of one object with the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> property of the other.</span></span> <span data-ttu-id="22141-106">Começando com aplicativos que direcionam o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], o método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> compara a propriedade <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> dos dois objetos.</span><span class="sxs-lookup"><span data-stu-id="22141-106">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method compares the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> property of the two objects.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="22141-107">Impacto</span><span class="sxs-lookup"><span data-stu-id="22141-107">Impact</span></span>  
 <span data-ttu-id="22141-108">Essa alteração implementa corretamente o teste de igualdade para objetos <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> e deve ter um impacto mínimo.</span><span class="sxs-lookup"><span data-stu-id="22141-108">This change correctly implements the test for equality for <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> objects and should have minimal impact.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="22141-109">Redução</span><span class="sxs-lookup"><span data-stu-id="22141-109">Mitigation</span></span>  
 <span data-ttu-id="22141-110">Duas soluções alternativas estarão disponíveis se o seu aplicativo direcionar o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou uma versão posterior do .NET Framework e ela depender do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> que às vezes retornará `false` quando os descritores de membro forem equivalentes:</span><span class="sxs-lookup"><span data-stu-id="22141-110">Two workarounds are available if your app targets the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or a later version of the .NET Framework and it depends on the  <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method sometimes returning `false` when member descriptors are equivalent:</span></span>  
  
-   <span data-ttu-id="22141-111">Você pode recusar essa alteração sem modificar seu código-fonte adicionando o seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="22141-111">You can opt out of this change without modifying your source code by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
    ```  
  
-   <span data-ttu-id="22141-112">É possível modificar seu código-fonte para restaurar o comportamento anterior comparando manualmente as propriedades <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> e <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> após chamar o método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>, como o fragmento de código a seguir faz.</span><span class="sxs-lookup"><span data-stu-id="22141-112">You can modify your source code to restore the previous behavior by manually comparing the  <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> and <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> properties after calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method, as the following code fragment does.</span></span>  
  
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
  
 <span data-ttu-id="22141-113">Para aplicativos direcionados ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e em versões anteriores, você pode habilitar essa alteração adicionando o seguinte valor ao seu arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="22141-113">For apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, you can enable this change by adding the following value to your app.config file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22141-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22141-114">See Also</span></span>  
 <span data-ttu-id="22141-115">[Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md) </span><span class="sxs-lookup"><span data-stu-id="22141-115">[Retargeting Changes](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md) </span></span>  
 [<span data-ttu-id="22141-116">Compatibilidade de aplicativos no 4.6.2</span><span class="sxs-lookup"><span data-stu-id="22141-116">Application Compatibility in 4.6.2</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)

