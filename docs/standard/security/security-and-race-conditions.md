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
ms.openlocfilehash: fdfc4d9e9ba3653bd1a762767e3c39a4f62e587a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-race-conditions"></a>Segurança e condições de corrida
Outra área de interesse é a possibilidade de falhas de segurança explorado por condições de corrida. Há várias maneiras em que isso pode acontecer. Os seguintes subtópicos descrevem algumas das principais armadilhas que o desenvolvedor deve evitar.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Condições de corrida no método Dispose  
 Se uma classe **Dispose** método (para obter mais informações, consulte [coleta de lixo](../../../docs/standard/garbage-collection/index.md)) não é sincronizada, é possível que o código de limpeza dentro de **Dispose** pode ser executado mais de vez, conforme mostrado no exemplo a seguir.  
  
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
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 Porque isso **Dispose** implementação não está sincronizada, é possível `Cleanup` a ser chamado pelo primeiro um thread e, em seguida, um thread de segundo antes `_myObj` é definido como **nulo**. Se isso for uma preocupação de segurança depende do que acontece quando o `Cleanup` código é executado. Um grande problema com sincronizado **Dispose** implementações envolve o uso de identificadores de recursos, como arquivos. Descarte inadequado pode fazer com que o identificador incorreto para ser usada, que geralmente leva a vulnerabilidades de segurança.  
  
## <a name="race-conditions-in-constructors"></a>Condições de corrida em construtores  
 Em alguns aplicativos, pode ser possível para outros threads para acessar membros de classe antes de executaram completamente seus construtores de classe. Você deve revisar todos os construtores de classe para certificar-se de que não há nenhum problema de segurança se isso deve acontecer ou sincronizar threads, se necessário.  
  
## <a name="race-conditions-with-cached-objects"></a>Condições de corrida com objetos armazenados em cache  
 Código que armazena informações de segurança ou usa a segurança de acesso do código [Assert](../../../docs/framework/misc/using-the-assert-method.md) operação também pode ser vulnerável a condições de corrida se outras partes da classe não estão sincronizados corretamente, conforme mostrado no exemplo a seguir.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
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
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
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
  
 Se não houver outros caminhos para `DoOtherWork` que pode ser chamado de outro thread com o mesmo objeto, um chamador não confiável pode ser adiada uma demanda passada.  
  
 Se seu código armazena em cache as informações de segurança, certifique-se de que você examine para essa vulnerabilidade.  
  
## <a name="race-conditions-in-finalizers"></a>Condições de corrida em finalizadores  
 Condições de corrida também podem ocorrer em um objeto que faz referência a um recurso estático ou não gerenciado que, em seguida, libera no seu finalizador. Se vários objetos compartilharem um recurso que é manipulado no finalizador da classe, os objetos devem sincronizar todo o acesso a esse recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
