---
title: Instrução Using (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: fd553430e56bbc5c21c9bdb25fc6b67eea530739
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595390"
---
# <a name="using-statement-visual-basic"></a>Instrução Using (Visual Basic)
Declara o início de um `Using` bloquear e, opcionalmente, adquire os recursos do sistema que controla o bloco.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`resourcelist`|Necessário se você não fornecer `resourceexpression`. Lista de um ou mais recursos do sistema que este `Using` bloquear controles, separados por vírgulas.|  
|`resourceexpression`|Necessário se você não fornecer `resourcelist`. Referência variável ou expressão referindo-se a um recurso do sistema para ser controlados por este `Using` bloco.|  
|`statements`|Opcional. Bloco de instruções que o `Using` execução do bloco.|  
|`End Using`|Necessário. Finaliza a definição do `Using` bloco e descarta todos os recursos que ele controla.|  
  
 Cada recurso no `resourcelist` parte tem a seguinte sintaxe e partes:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 -ou-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>Partes de resourcelist  
  
|Termo|Definição|  
|---|---|  
|`resourcename`|Necessário. Variável de referência que se refere a um recurso do sistema que o `Using` bloquear os controles.|  
|`New`|Obrigatório se o `Using` instrução adquire o recurso. Se você já tenha adquirido o recurso, use a segunda sintaxe alternativa.|  
|`resourcetype`|Necessário. A classe do recurso. A classe deve implementar o <xref:System.IDisposable> interface.|  
|`arglist`|Opcional. Lista de argumentos que você está passando para o construtor para criar uma instância de `resourcetype`. Ver [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Necessário. Variável ou expressão referindo-se a um recurso do sistema que satisfazem os requisitos de `resourcetype`. Se você usar a segunda sintaxe alternativa, você deve adquirir o recurso antes de passar o controle para o `Using` instrução.|  
  
## <a name="remarks"></a>Comentários  
 Às vezes, seu código requer um recurso não gerenciado, como um identificador de arquivo, um wrapper COM ou uma conexão SQL. Um `Using` bloco garante a disposição de um ou mais dos tais recursos quando seu código for concluído com eles. Isso os torna disponíveis para outro código para usar.  
  
 Recursos gerenciados sejam descartados pelo coletor de lixo do .NET Framework (GC) sem qualquer codificação extra de sua parte. Não é necessário um `Using` bloco para os recursos gerenciados. No entanto, você ainda pode usar um `Using` bloco para forçar o descarte de um recurso gerenciado em vez de esperar o coletor de lixo.  
  
 Um `Using` bloco tem três partes: aquisição, uso e descarte.  
  
-   *Aquisição* significa criar uma variável e inicializá-la para se referir ao recurso do sistema. O `Using` instrução pode adquirir um ou mais recursos, ou você pode adquirir exatamente um recurso antes de inserir o bloco e fornecê-lo para o `Using` instrução. Se você fornecer `resourceexpression`, você deve adquirir o recurso antes de passar o controle para o `Using` instrução.  
  
-   *Uso* significa acessar os recursos e executar ações com eles. As instruções entre `Using` e `End Using` representam o uso de recursos.  
  
-   *Disposição* significa que a chamada a <xref:System.IDisposable.Dispose%2A> método no objeto do `resourcename`. Isso permite que o objeto libere corretamente seus recursos. O `End Using` instrução descarta os recursos sob o `Using` controle bloco de.  
  
## <a name="behavior"></a>Comportamento  
 Um `Using` bloco se comporta como um `Try`... `Finally` em que o `Try` block usa os recursos e o `Finally` bloco descarta-los. Por isso, o `Using` bloco garante a liberação dos recursos, não importa como você sai do bloco. Isso é verdadeiro mesmo no caso de uma exceção sem tratamento, exceto para um <xref:System.StackOverflowException>.  
  
 O escopo de cada recurso variável adquirido pelo `Using` instrução é limitada ao `Using` bloco.  
  
 Se você especificar mais de um recurso do sistema na `Using` instrução, o efeito é o mesmo como se você aninhado `Using` bloqueia uma dentro de outra.  
  
 Se `resourcename` está `Nothing`, nenhuma chamada para <xref:System.IDisposable.Dispose%2A> é feita, e nenhuma exceção é lançada.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Tratamento dentro de um bloco de uso de exceções estruturado  
 Se você precisar manipular uma exceção que pode ocorrer dentro de `Using` bloco, você pode adicionar uma completa `Try`... `Finally` concluída a ela. Se você precisar manipular o caso em que o `Using` instrução não for bem-sucedido ao adquirir um recurso, você pode testar para ver se `resourcename` é `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Tratamento em vez de um bloco de uso de exceções estruturado  
 Se você precisar ter maior controle sobre a aquisição dos recursos, ou você precisa de código adicional na `Finally` bloco, você pode reescrever a `Using` bloquear como um `Try`... `Finally` construção. O exemplo a seguir mostra o esqueleto `Try` e `Using` construções que são equivalentes na aquisição e liberação de `resource`.  
  
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
>  O código dentro de `Using` bloco não deve atribuir o objeto `resourcename` a outra variável. Quando você fechar o `Using` bloco, o recurso é descartado, e a outra variável não é possível acessar o recurso para o qual ele aponta.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um arquivo que é chamado de log. txt e grava duas linhas de texto no arquivo. O exemplo também lê esse mesmo arquivo e exibe as linhas de texto.  
  
 Porque o <xref:System.IO.TextWriter> e <xref:System.IO.TextReader> classes implementam a <xref:System.IDisposable> interface, o código pode usar `Using` instruções para garantir que o arquivo seja fechado após a gravação corretamente e operações de leitura.  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.IDisposable>
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Como: Descartar um recurso do sistema](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
