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
ms.openlocfilehash: 8980122acdd069bc840aa09129483a1cb9a379fd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705867"
---
# <a name="security-and-race-conditions"></a>Segurança e condições de corrida
Outra área de preocupação é o potencial de brechas de segurança exploradas por condições de corrida. Há várias maneiras pelas quais isso pode acontecer. Os subtópicos a seguir descrevem algumas das principais armadilhas que o desenvolvedor deve evitar.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Condições de corrida no método Dispose  
 Se o método **Dispose** de uma classe (para obter mais informações, consulte [coleta de lixo](../../../docs/standard/garbage-collection/index.md)) não estiver sincronizado, é possível que o código de limpeza dentro de **Dispose** possa ser executado mais de uma vez, conforme mostrado no exemplo a seguir.  
  
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
  
 Como essa implementação **Dispose** não é sincronizada, é possível que `Cleanup` seja chamado pelo primeiro thread e, depois, por um segundo thread antes que `_myObj` seja definido como **NULL**. Se essa é uma preocupação de segurança depende do que acontece quando o código de `Cleanup` é executado. Um grande problema com implementações de **Dispose** não sincronizadas envolve o uso de identificadores de recursos, como arquivos. A alienação imprópria pode fazer com que o identificador errado seja usado, o que geralmente leva a vulnerabilidades de segurança.  
  
## <a name="race-conditions-in-constructors"></a>Condições de corrida em construtores  
 Em alguns aplicativos, pode ser possível que outros threads acessem os membros da classe antes que seus construtores de classe tenham sido executados completamente. Você deve examinar todos os construtores de classe para garantir que não haja problemas de segurança se isso ocorrer ou sincronizar threads, se necessário.  
  
## <a name="race-conditions-with-cached-objects"></a>Condições de corrida com objetos armazenados em cache  
 O código que armazena em cache informações de segurança ou usa a operação de [declaração](../../../docs/framework/misc/using-the-assert-method.md) de segurança de acesso ao código também pode ser vulnerável a condições de corrida se outras partes da classe não estiverem sincronizadas adequadamente, conforme mostrado no exemplo a seguir.  
  
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
  
 Se houver outros caminhos para `DoOtherWork` que podem ser chamados de outro thread com o mesmo objeto, um chamador não confiável poderá passar por uma demanda.  
  
 Se o código armazenar em cache as informações de segurança, certifique-se de analisá-las para essa vulnerabilidade.  
  
## <a name="race-conditions-in-finalizers"></a>Condições de corrida em finalizadores  
 As condições de corrida também podem ocorrer em um objeto que faz referência a um recurso estático ou não gerenciado que ele libera em seu finalizador. Se vários objetos compartilharem um recurso que é manipulado no finalizador de uma classe, os objetos deverão sincronizar todo o acesso a esse recurso.  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
