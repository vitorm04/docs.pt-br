---
title: "Processamento de aplicativos com a política"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86c7890af651ba9f0ee0ec2a1763f9c579bac89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="order-processing-with-policy"></a>Processamento de aplicativos com a política
O exemplo de política de processamento de aplicativos demonstra alguns dos principais recursos introduzidos em [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] do Windows Workflow Foundation (WF). A seguinte funcionalidade é novo para o mecanismo de regras WF:  
  
-   Suporte para a sobrecarga de operador.  
  
-   Suporte para o operador de `new` , permitindo que os usuários criem novos objetos e matrizes de regras WF.  
  
-   Suporte para que os métodos de extensão da experiência do usuário em chamando métodos de extensão de regras WF compatível com os estilos de codificação C#.  
  
> [!NOTE]
>  Esse exemplo requer que [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] está instalado para compilar e executar. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] é necessário para abrir arquivos de projeto e de solução.  
  
 O exemplo demonstra um projeto de `OrderProcessingPolicy` a que um pedido de cliente, que consiste em uma lista numerada de itens disponíveis e um código postal, é inserido. A ordem é processado com êxito se ambas as entradas estão corretas; caso contrário, a diretiva cria objetos de erro, utilizando um operador sobrecarregado de `+` e um método de extensão predefinido para informar ao usuário de erros.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]métodos de extensão, consulte [c# versão 3.0 especificação](http://go.microsoft.com/fwlink/?LinkId=95402).  
  
 O exemplo é composto de projetos seguintes:  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` é uma biblioteca de classe que define `OrderError` e classes de `OrderErrorCollection` . Uma instância de `OrderError` é criada quando uma entrada inválida está inserido. A biblioteca também fornece um método de extensão na classe de `OrderErrorCollection` a saída a propriedade de `ErrorText` em todos os objetos de `OrderError` em `OrderErrorCollection`.  
  
-   `OrderProcessingPolicy`  
  
     O projeto de `OrderProcessingPolicy` é um aplicativo de console de WF que define uma única atividade de `PolicyFromFile` . A atividade tem as seguintes regras:  
  
    -   `invalidItemNum`  
  
         Essa regra que valida o número de item está entre 1 e 6, inclusive. Se o número de item está dentro do intervalo válido, a regra não fará nada (diferente da impressão no console). Se o número de item não está entre 1 e 6, a regra de `invalidItemNum` faz o seguinte:  
  
        1.  Cria um novo objeto de `OrderError` , passando o número de item inserido, e defina as propriedades de `ErrorText` e de `CustomerName` no objeto.  
  
        2.  Cria um objeto de `invalidItemNumErrorCollection` .  
  
        3.  Adicione a instância recém-criado de `OrderError` a `invalidItemNumErrorCollection`.  
  
         Isso demonstra suporte para o operador de `new` , com o qual você pode instanciar objetos dentro das regras.  
  
    -   `invalidZip`  
  
         Essa regra valida que o código postal tem 5 dígitos, e está no intervalo de 600 a 99998. Se o código postal está dentro do intervalo válido, a regra não fará nada (diferente da impressão no console). Se o comprimento do código postal é menor que 5, ou o código postal não está entre 00600 e 99998, a regra de `invalidZip` faz o seguinte:  
  
        1.  Cria um objeto de `OrderError` , passando o código postal inserido, e defina as propriedades de `ErrorText` e de `CustomerName` no objeto.  
  
        2.  Cria um objeto de `invalidZipCodeErrorCollection` .  
  
        3.  Adicione a instância recém-criado de `OrderError` a `invalidZipCodeErrorCollection`recém-criado.  
  
         Essa regra demonstra novamente suporte para o operador de `new` , que permite que você crie uma instância de objetos dentro das regras.  
  
    -   `displayErrors`  
  
         Essa regra verifica para ver se houver erros adicionado por duas regras anteriores dos dois objetos `OrderErrorCollection` e `invalidItemNumErrorCollection`de `invalidIZipCodeErrorCollection` . Se ocorreram erros ( `invalidItemNumErrorCollection` ou `invalidZipCodeErrorCollection` não são `null`), a regra faz o seguinte:  
  
        1.  Chama o sobrecarregado `+` operador para copiar o conteúdo de `invalidItemNumErrorCollection` e `invalidZipCodeErrorCollection` para um `invalidOrdersCollection``OrderErrorCollection` instância.  
  
        2.  Chama o método de extensão de `PrintOrderErrors` em `invalidOrdersCollection` e saída que a propriedade de `ErrorText` em qualquer `orderError` objetos em `invalidOrdersCollection`.  
  
 O operador sobrecarregado `+` em `OrderErrorCollection` é definido na classe de `OrderErrorCollection` , no projeto de `OrderErrorLibrary` . Leva dois objetos de `OrderErrorCollection` e os combina em um objeto de `OrderErrorCollection` .  
  
 O método de extensão de `PrintOrderErrors` também é definido no projeto de `OrderErrorLibrary` . Métodos de extensão é um novo recurso C# que habilita os desenvolvedores para adicionar novos métodos ao contrato pública de um tipo existente de CLR, sem ter que derivar uma classe deles ou recompilar o tipo original.  
  
 Quando você executa o exemplo você será solicitado para digitar um nome, ao número de item de item a ser comprado, e um código postal. Essa informação é verificada nas regras definidas na atividade de política. O seguinte é saída de exemplo do programa.  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o arquivo de projeto de OrderProcessingPolicy.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Há dois diferentes projetos na solução: `OrderErrorLibrary` e `OrderProcessingPolicy`. As classes e métodos dos usos de projeto de `OrderProcessingPolicy` definidos em `OrderErrorLibrary`.  
  
3.  Compilar todos os projetos.  
  
4.  Clique em **Executar**.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`