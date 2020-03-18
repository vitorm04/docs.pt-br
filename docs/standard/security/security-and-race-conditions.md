---
title: Segurança e condições de corrida
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186789"
---
# <a name="security-and-race-conditions"></a>Segurança e condições de corrida
Outra área de preocupação é o potencial de falhas de segurança exploradas pelas condições raciais. Há várias maneiras pelas quais isso pode acontecer. Os subtópicos que seguem descrevem algumas das principais armadilhas que o desenvolvedor deve evitar.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Condições de corrida no método de descarte  
 Se o método **Descarte** de uma classe (para obter mais informações, consulte [Coleta de Lixo](../../../docs/standard/garbage-collection/index.md)) não estiver sincronizado, é possível que o código de limpeza dentro de **Dispose** possa ser executado mais de uma vez, como mostrado no exemplo a seguir.  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()
{  
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 Como esta **implementação Descartar** não está `Cleanup` sincronizada, é possível ser chamado por `_myObj` primeiro thread e, em seguida, um segundo segmento antes de ser definido como **nulo**. Se isso é uma preocupação de `Cleanup` segurança depende do que acontece quando o código é executado. Um grande problema com **implementações de descarte** não sincronizadas envolve o uso de alças de recursos, como arquivos. O descarte inadequado pode fazer com que o cabo errado seja usado, o que muitas vezes leva a vulnerabilidades de segurança.  
  
## <a name="race-conditions-in-constructors"></a>Condições de corrida em Construtores  
 Em alguns aplicativos, pode ser possível que outros segmentos acessem os membros da classe antes que seus construtores de classe sejam completamente executados. Você deve rever todos os construtores de classe para ter certeza de que não há problemas de segurança se isso acontecer, ou sincronizar threads, se necessário.  
  
## <a name="race-conditions-with-cached-objects"></a>Condições de corrida com objetos armazenados em cache  
 Código que armazena informações de segurança ou usa a segurança de acesso ao código A operação [assert](../../../docs/framework/misc/using-the-assert-method.md) também pode ser vulnerável a condições de corrida se outras partes da classe não estiverem adequadamente sincronizadas, como mostrado no exemplo a seguir.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()
{  
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
    {  
        DoSomethingTrusted();  
    }  
    else
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 Se houver outros `DoOtherWork` caminhos para isso que podem ser chamados de outro segmento com o mesmo objeto, um chamador não confiável pode passar por uma demanda.  
  
 Se o seu código armazena informações de segurança, certifique-se de revisá-la para essa vulnerabilidade.  
  
## <a name="race-conditions-in-finalizers"></a>Condições de corrida em finalizadores  
 As condições de corrida também podem ocorrer em um objeto que faz referência a um recurso estático ou não gerenciado que ele então libera em seu finalizador. Se vários objetos compartilharem um recurso manipulado no finalizador de uma classe, os objetos devem sincronizar todo o acesso a esse recurso.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
