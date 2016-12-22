---
title: "Instru&#231;&#227;o Using (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.using"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "eliminação de recurso"
  - "recursos [Visual Basic], descarte"
  - "instruções Try...Catch...Finally, equivalente à instrução Using"
  - "instrução Using"
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: 36
caps.handback.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Using (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara o início de um bloco `Using` e opcionalmente adquire os recursos do sistema que o bloco controla.  
  
## Sintaxe  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`resourcelist`|Necessário se você não fornecer `resourceexpression`.  Lista de um ou mais recursos do sistema que controles de este bloco de `Using` , separada por vírgulas.|  
|`resourceexpression`|Necessário se você não fornecer `resourcelist`.  Variável ou expressão de referência referem\-se a um recurso do sistema controlado por este bloco `Using`.|  
|`statements`|Opcional.  Bloco de instruções executadas pelo bloco `Using`.|  
|`End Using`|Obrigatório.  Finaliza a definição do bloco `Using` e disponibiliza todos os recursos que ele controla.|  
  
 Cada recurso na parte `resourcelist` possui a seguinte sintaxe e partes:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 \-  ou  \-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## Partes resourcelist  
  
|||  
|-|-|  
|Termo|Definição|  
|`resourcename`|Obrigatório.  Variável que faz referência a um recurso do sistema que controlado pelo bloco `Using`.|  
|`New`|Necessário se a instrução `Using` adquire o recurso.  Se você já tiver adquirido o recurso, use a segunda sintaxe alternativa.|  
|`resourcetype`|Obrigatório.  A classe do recurso.  A classe deve implementar a interface <xref:System.IDisposable>.|  
|`arglist`|Opcional.  Lista de argumentos que você está passando para o construtor para criar uma instância de `resourcetype`.  Consulte [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Obrigatório.  Variável ou expressão referindo\-se a um recurso de sistema que satisfaz os requisitos do `resourcetype`.  Se você usar a segunda sintaxe alternativa, você deve adquirir o recurso antes de passar controle para a instrução `Using`.|  
  
## Comentários  
 Às vezes, seu código requer um recurso não gerenciado, como um identificador de arquivo, um wrapper COM ou uma conexão SQL.  Um bloco `Using`garante a disposição de um ou mais dos tais recursos quando seu código estiver finalizado com eles.  Isso torna\-os disponíveis para uso por outros códigos.  
  
 Recursos gerenciados são descartados pela coletor de lixo .NET Framework \(GC\) sem qualquer codificação extra de sua parte.  Você não precisa de um bloco `Using`para recursos gerenciados.  Em o entanto, você ainda pode usar um bloco de `Using` para forçar a disponibilidade de um recurso gerenciado em vez de espera o coletor de lixo.  
  
 Um bloco `Using`possui três partes: a aquisição, uso e descarte.  
  
-   *Aquisição*  significa criar uma variável e inicializá\-la para se referir ao recurso do sistema.  A instrução `Using` pode adquirir um ou mais recursos, ou você pode adquirir exatamente um recurso antes de inserir o bloco e fornece\-lo para a instrução `Using`.  Se você fornecer `resourceexpression`, você deve adquirir o recurso antes de passar controle para a instrução `Using`.  
  
-   *Usage*  significa acessar os recursos e executar ações com eles.  As instruções entre `Using` e `End Using` representam o uso de recursos.  
  
-   *Descarte*  significa chamar o método <xref:System.IDisposable.Dispose%2A> no objeto em `resourcename`.  Isso permite que o objeto libere corretamente seus recursos.  A instrução `End Using` libera os recursos sob o bloco de controle `Using`.  
  
## Comportamento  
 Um bloco `Using`se comporta como uma construção `Try`... `Finally` em que o bloco `Try` usa os recursos e o bloco `Finally` os libera.  Devido a isso, o bloco `Using` garante a liberação dos recursos, não importando como você sai do bloco.  Isso é verdadeiro mesmo no caso de uma exceção sem tratamento, exceto por <xref:System.StackOverflowException>.  
  
 O escopo de cada recurso variável adquirido pela instrução `Using` é limitado para o bloco `Using`.  
  
 Se você especificar mais de um recurso do sistema na instrução `Using`, o efeito é o mesmo como se você tivesse blocos `Using` aninhados, um dentro do outro.  
  
 Se `resourcename` é `Nothing`, nenhuma chamada a <xref:System.IDisposable.Dispose%2A> é feito, e nenhuma exceção é lançada.  
  
## Tratamento de exceções estruturado num bloco Using  
 Se você precisar manipular uma exceção que pode ocorrer dentro de um bloco `Using`, é possível adicionar uma construção `Try` ... `Finally` concluída a ela.  Se você precisar manipular o caso em que a instrução `Using` não for bem\-sucedida em adquirir um recurso, você pode testar para verificar se `resourcename` é `Nothing`.  
  
## Tratamento de Exceção Estruturado em ves de usar um bloco Using  
 Se você precisar exercer um melhor controle sobre a aquisição dos recursos, ou se precisar de código adicional no bloco `Finally` , você pode reescrever o bloco `Using` como uma construção `Try`. .. `Finally`.  O exemplo a seguir mostra construções `Try` esqueleto e `Using` que são equivalentes na aquisição e liberação de `resource`.  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  O código dentro do bloco `Using`não deve atribuir o objeto `resourcename` a outra variável.  Quando você sai do bloco `Using`, o recurso é descartado, e a outra variável não pode acessar o recurso para o qual ela aponta.  
  
## Exemplo  
 O exemplo a seguir cria um arquivo chamado log.txt e grava duas linhas de texto para o arquivo.  O exemplo também ler o mesmo arquivo e exibe as linhas de texto.  
  
 Porque as classes de <xref:System.IO.TextWriter> e de <xref:System.IO.TextReader> implementam a interface de <xref:System.IDisposable> , o código pode usar instruções de `Using` para garantir que o arquivo é encerrado corretamente após a gravação e operações de leitura.  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## Consulte também  
 <xref:System.IDisposable>   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Como descartar um recurso do sistema](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)