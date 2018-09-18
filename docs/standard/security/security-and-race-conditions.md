---
title: Segurança e condições de corrida
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991045"
---
# <a name="security-and-race-conditions"></a>Segurança e condições de corrida
Outra área de interesse é o potencial para brechas de segurança exploradas por condições de corrida. Há várias maneiras em que isso pode acontecer. Os subtópicos seguir descrevem algumas das principais armadilhas que o desenvolvedor deve evitar.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Condições de corrida no método Dispose  
 Se uma classe **Dispose** método (para obter mais informações, consulte [coleta de lixo](../../../docs/standard/garbage-collection/index.md)) não é sincronizado, é possível esse código de limpeza dentro **Dispose** pode ser executado mais de uma vez, conforme mostrado no exemplo a seguir.  
  
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
  
 Porque isso **Dispose** implementação não está sincronizada, é possível `Cleanup` a ser chamado pelo primeiro um thread e, em seguida, um segundo thread antes `_myObj` está definido como **nulo**. Se esta é uma preocupação de segurança depende do que acontece quando o `Cleanup` código é executado. Um grande problema com não sincronizadas **Dispose** implementações envolve o uso de identificadores de recurso, como arquivos. Descarte inadequado pode fazer com que o identificador errado a ser usado, o que muitas vezes leva a vulnerabilidades de segurança.  
  
## <a name="race-conditions-in-constructors"></a>Condições de corrida em construtores  
 Em alguns aplicativos, pode ser possível que outros threads acessar membros de classe antes de executaram completamente seus construtores de classe. Você deve examinar todos os construtores de classe para certificar-se de que não há nenhum problema de segurança se isso deve acontecer ou sincronizar threads, se necessário.  
  
## <a name="race-conditions-with-cached-objects"></a>Condições de corrida com objetos armazenados em cache  
 Código que armazena em cache informações de segurança ou usa a segurança de acesso do código [Assert](../../../docs/framework/misc/using-the-assert-method.md) operação também pode ser vulnerável a condições de corrida se outras partes da classe não estão sincronizados corretamente, conforme mostrado no exemplo a seguir.  
  
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
  
 Se houver outros caminhos para `DoOtherWork` que podem ser chamados de outro thread com o mesmo objeto, um chamador não confiável pode ser adiada uma demanda passada.  
  
 Se seu código armazena em cache informações de segurança, certifique-se de que você examine essa vulnerabilidade.  
  
## <a name="race-conditions-in-finalizers"></a>Condições de corrida em finalizadores  
 Condições de corrida também podem ocorrer em um objeto que faz referência a um recurso estático ou não gerenciado que ele libera, em seguida, no seu finalizador. Se vários objetos compartilham um recurso que é manipulado no finalizador de uma classe, os objetos devem sincronizar todo o acesso a esse recurso.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
