---
title: "Vari&#225;vel de objeto ou vari&#225;vel com bloco n&#227;o definida | Microsoft Docs"
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
  - "vbrID91"
dev_langs: 
  - "VB"
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;vel de objeto ou vari&#225;vel com bloco n&#227;o definida
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma variável de objeto inválida está sendo referenciada.   Esse erro pode ocorrer por diversos motivos:  
  
-   Uma variável foi declarada sem especificar um tipo. Se uma variável é declarada sem especificar um tipo, ele assume como padrão para o tipo `Object`.  
  
     Por exemplo, uma variável declarada com `Dim x` seria do tipo `Object;` uma variável declarada com `Dim x As String` seria do tipo `String`.  
  
    > [!TIP]
    >  O `Option Strict` instrução não permite a digitação implícita que resulta em um `Object` tipo. Se você omitir o tipo, ocorrerá um erro de tempo de compilação. Consulte [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Você está tentando fazer referência a um objeto que foi definido como `Nothing`  
  
     .  
  
-   Você está tentando acessar um elemento de uma variável de matriz não foi declarado corretamente.  
  
     Por exemplo, uma matriz declarada como `products() As String` irá disparar o erro se você tentar fazer referência a um elemento da matriz `products(3) = "Widget"`. A matriz não tem elementos e é tratada como um objeto.  
  
-   Tentativa de acesso de código dentro de um `With...End With` Bloquear antes que o bloco foi inicializado.   Um `With...End With` deve ser inicializado executando o `With` ponto de entrada da declaração.  
  
> [!NOTE]
>  Em versões anteriores do Visual Basic ou VBA esse erro também foi disparado, atribuindo um valor a uma variável sem usar o `Set` palavra\-chave \(`x = "name"` em vez de `Set x = "name"`\). O `Set` palavra\-chave não é válido no Visual Basic .net.  
  
### Para corrigir este erro  
  
1.  Defina `Option Strict` para `On` adicionando o seguinte código ao início do arquivo:  
  
    ```vb  
    Option Strict On  
    ```  
  
     Quando você executa o projeto, um erro do compilador aparecerá no **Error List** para qualquer variável que foi especificado sem um tipo.  
  
2.  Se você não quiser habilitar `Option Strict`, pesquise o código para todas as variáveis que foram especificadas sem um tipo \(`Dim x` em vez de `Dim x As String`\) e adicione o tipo desejado para a declaração.  
  
3.  Verifique se você não está fazendo referência a uma variável de objeto que foi definida como `Nothing`.  Pesquise o código para a palavra\-chave `Nothing`, e revisar seu código para que o objeto não está definida como `Nothing` até que, depois de você ter referenciado.  
  
4.  Certifique\-se de que quaisquer variáveis de matriz são dimensionadas para acessá\-los. É possível atribuir uma dimensão quando você cria a matriz \(`Dim x(5) As String` em vez de `Dim x() As String`\), ou use o `ReDim` palavra\-chave para definir as dimensões da matriz antes de acessar pela primeira vez.  
  
5.  Verifique se o `With` bloco é inicializado executando o `With` ponto de entrada da declaração.  
  
## Consulte também  
 [Declaração de variável do objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)