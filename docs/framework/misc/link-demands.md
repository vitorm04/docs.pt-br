---
title: Demandas de link
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: faeeabeda89ea233e67b66b8848f5bbb665d3804
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="link-demands"></a>Demandas de link
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Uma demanda de link faz com que uma verificação de segurança durante a compilação just-in-time e verifica somente o assembly de chamada imediato do seu código. Vinculando ocorre quando seu código é associado a uma referência de tipo, incluindo referências de ponteiro de função e chamadas de método. Se o assembly de chamada não tem permissão suficiente para vincular ao seu código, o link não é permitido e uma exceção de tempo de execução é gerada quando o código é carregado e executado. Demandas de link podem ser substituídas nas classes que herdam de seu código.  
  
 Observe que um exame da pilha completa não será executado com esse tipo de demanda e que seu código ainda é suscetível a ataques de atração. Por exemplo, se um método no assembly A é protegido por uma demanda de link, um chamador direto no assembly B é avaliado com base nas permissões do Assembly B.  No entanto, a demanda de link não avaliará um método no assembly C se indiretamente chama o método no assembly usando o método no assembly B. A demanda de link Especifica que apenas as permissões de direcionam os chamadores no assembly de chamada imediato devem ter que vincular ao seu código. Ele não especifica as permissões de todos os chamadores devem ter para executar seu código.  
  
 O <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, e <xref:System.Security.CodeAccessPermission.PermitOnly%2A> modificadores de movimentação de pilha não afetam a avaliação de demandas de link.  Como as demandas de link não executam um exame da pilha, os modificadores de movimentação de pilha não têm efeito nas demandas de link.  
  
 Se um método protegido por uma demanda de link é acessado por meio de [reflexão](../../../docs/framework/reflection-and-codedom/reflection.md), em seguida, uma demanda de link verifica o chamador imediato do código acessado por meio de reflexão. Isso é verdadeiro para descoberta de método e executada usando a reflexão de invocação de método. Por exemplo, suponha que o código usa reflexão para retornar um <xref:System.Reflection.MethodInfo> do objeto que representa um método protegido por uma demanda de link e, em seguida, passa que **MethodInfo** objeto para algum outro código que usa o objeto para invocar o método original. Nesse caso a verificação de demanda de link ocorre duas vezes: uma vez para o código que retorna o **MethodInfo** objeto e uma vez para o código que o chama.  
  
> [!NOTE]
>  Uma demanda de link executada em um construtor de classe estática não protege o construtor porque construtores estáticos são chamados pelo sistema, fora do caminho de execução de código do aplicativo. Como resultado, quando uma demanda de link é aplicada a uma classe inteira, ele não pode proteger o acesso a um construtor estático, embora ele protege o restante da classe.  
  
 O fragmento de código a seguir declarativamente Especifica que qualquer código de vinculação para o `ReadData` método deve ter o `CustomPermission` permissão. Essa permissão é uma permissão personalizada hipotética e não existe no .NET Framework. A solicitação é feita, passando um **SecurityAction.LinkDemand** sinalizador como o `CustomPermissionAttribute`.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Atributos](../../../docs/standard/attributes/index.md)  
 [Segurança de acesso do código](../../../docs/framework/misc/code-access-security.md)
