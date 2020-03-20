---
title: Demandas de link
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181167"
---
# <a name="link-demands"></a>Demandas de link
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Uma demanda de link causa uma verificação de segurança durante a compilação just-in-time e verifica apenas a montagem imediata de chamada do seu código. A vinculação ocorre quando seu código está vinculado a uma referência de tipo, incluindo referências de ponteiro de função e chamadas de método. Se a assembléia de chamada não tiver permissão suficiente para vincular ao seu código, o link não é permitido e uma exceção em tempo de execução é lançada quando o código é carregado e executado. As demandas de link podem ser substituídas em classes que herdam do seu código.  
  
 Observe que uma caminhada de pilha completa não é realizada com esse tipo de demanda e que seu código ainda é suscetível a atrair ataques. Por exemplo, se um método na montagem A for protegido por uma demanda de link, um chamador direto no conjunto B será avaliado com base nas permissões da Assembléia B.  No entanto, a demanda de link não avaliará um método na montagem C se ele chamar indiretamente o método na montagem A usando o método na montagem B. A demanda de link especifica apenas as permissões que os chamadores diretos na assembléia de chamada imediata devem ter que vincular ao seu código. Ele não especifica as permissões que todos os chamadores devem ter para executar seu código.  
  
 Os <xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.CodeAccessPermission.Deny%2A>modificadores <xref:System.Security.CodeAccessPermission.PermitOnly%2A> de caminhada e pilha não afetam a avaliação das demandas de link.  Como as demandas de link não realizam uma caminhada de pilha, os modificadores de caminhada de pilha não têm efeito sobre as demandas de link.  
  
 Se um método protegido por uma demanda de link for acessado através do [Reflection,](../reflection-and-codedom/reflection.md)então uma demanda de link verifica o chamador imediato do código acessado através da reflexão. Isso é verdade tanto para a descoberta do método quanto para a invocação do método realizada com reflexão. Por exemplo, suponha que <xref:System.Reflection.MethodInfo> o código use reflexão para retornar um objeto representando um método protegido por uma demanda de link e, em seguida, passa esse objeto **MethodInfo** para algum outro código que usa o objeto para invocar o método original. Neste caso, a verificação de demanda de link ocorre duas vezes: uma para o código que retorna o objeto **MethodInfo** e outra para o código que o invoca.  
  
> [!NOTE]
> Uma demanda de link realizada em um construtor de classe estática não protege o construtor porque os construtores estáticos são chamados pelo sistema, fora do caminho de execução de código do aplicativo. Como resultado, quando uma demanda de link é aplicada a uma classe inteira, ela não pode proteger o acesso a um construtor estático, embora proteja o resto da classe.  
  
 O fragmento de código a seguir especifica declarativamente que qualquer código vinculado ao `ReadData` método deve ter a `CustomPermission` permissão. Essa permissão é uma permissão personalizada hipotética e não existe no Quadro .NET. A demanda é feita passando uma bandeira **SecurityAction.LinkDemand** para o `CustomPermissionAttribute`.  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a>Confira também

- [Atributos](../../standard/attributes/index.md)
- [Segurança de acesso a código](code-access-security.md)
