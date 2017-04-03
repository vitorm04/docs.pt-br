---
title: "Como iterar em uma árvore de diretório (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c63e18bc7e23a9fda4a005745174bdd6c85b3f08
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Como iterar em uma árvore de diretório (Guia de Programação em C#)
A expressão "iterar uma árvore de diretório" significa acessar cada arquivo em cada subdiretório aninhado em uma pasta raiz especificada, em qualquer profundidade. Você não precisa necessariamente abrir cada arquivo. Você pode apenas recuperar o nome do arquivo ou subdiretório como um `string` ou pode recuperar informações adicionais na forma de um objeto <xref:System.IO.FileInfo?displayProperty=fullName> ou <xref:System.IO.DirectoryInfo?displayProperty=fullName>.  
  
> [!NOTE]
>  No Windows, os termos "diretório" e "pasta" são usados de forma intercambiável. A maior parte do texto da documentação e da interface do usuário usa o termo "pasta", mas a biblioteca de classes [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] usa o termo "diretório".  
  
 No caso mais simples, em que você sabe com certeza que tem permissões de acesso a todos os diretórios em uma raiz especificada, é possível usar o sinalizador `System.IO.SearchOption.AllDirectories`. Esse sinalizador retorna todos os subdiretórios aninhados que correspondem ao padrão especificado. O exemplo a seguir mostra como usar o sinalizador.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 As desvantagem dessa abordagem é que, se qualquer um dos subdiretórios na raiz especificada causar um <xref:System.IO.DirectoryNotFoundException> ou <xref:System.UnauthorizedAccessException>, o método inteiro falhará e não retornará nenhum diretório. O mesmo vale quando você usa o método <xref:System.IO.DirectoryInfo.GetFiles%2A>método. Se precisar manipular essas exceções em subpastas específicas, você precisa percorrer manualmente a árvore de diretório, conforme mostrado nos exemplos a seguir.  
  
 Quando percorre manualmente uma árvore de diretório, você pode manipular os subdiretórios primeiro (*passagem da pré-encomenda*) ou os arquivos primeiro (*passagem da pós-encomenda*). Se executar uma passagem da pré-encomenda, você percorre toda a árvore na pasta atual antes iterar nos arquivos que estão diretamente na própria pasta. Os exemplos mais adiante neste documento executam a passagem da pós-encomenda, mas você pode facilmente modificá-los para executar a passagem da pré-encomenda.  
  
 Outra opção é usar a recursão ou uma passagem baseada em pilha. Os exemplos mais adiante neste documento mostram as duas abordagens.  
  
 Se precisar executar uma série de operações em arquivos e pastas, você pode modularizar esses exemplos refatorando a operação em funções separadas que podem ser invocadas usando um único delegado.  
  
> [!NOTE]
>  Sistemas de arquivos NTFS podem conter *pontos de nova análise* na forma de *pontos de junção*, *links simbólicos* e *links físicos*. Os métodos do .NET Framework, como <xref:System.IO.DirectoryInfo.GetFiles%2A> e <xref:System.IO.DirectoryInfo.GetDirectories%2A>, não retornarão subdiretórios em um ponto de nova análise. Esse comportamento protege contra o risco de entrar em um loop infinito quando dois pontos de nova análise fazem referência um ao outro. De modo geral, você deve ter muito cuidado ao lidar com pontos de nova análise para garantir que arquivos não sejam modificados ou excluídos inadvertidamente. Se precisar ter um controle preciso sobre pontos de nova análise, use a invocação de plataforma ou código nativo para chamar diretamente os métodos apropriados do sistema de arquivos Win32.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como percorrer uma árvore de diretório usando a recursão. A abordagem recursiva é elegante, mas tem o potencial de causar uma exceção de estouro de pilha se a árvore de diretório for grande e profundamente aninhada.  
  
 As exceções específicas que são tratadas, bem como as ações específicas que são executadas em cada arquivo ou pasta, são fornecidas apenas como exemplo. Você deve modificar este código para atender às suas necessidades específicas. Consulte os comentários no código para obter mais informações.  
  
 [!code-cs[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como iterar em arquivos e pastas em uma árvore de diretório sem o uso de recursão. Essa técnica usa o tipo de coleção genérico <xref:System.Collections.Generic.Stack%601>, que é uma pilha UEPS (último a entrar, primeiro a sair).  
  
 As exceções específicas que são tratadas, bem como as ações específicas que são executadas em cada arquivo ou pasta, são fornecidas apenas como exemplo. Você deve modificar este código para atender às suas necessidades específicas. Consulte os comentários no código para obter mais informações.  
  
 [!code-cs[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 Geralmente, é muito demorado testar cada pasta para determinar se seu aplicativo tem permissão para abri-la. Portanto, o exemplo de código apenas coloca essa parte da operação em um bloco `try/catch`. É possível modificar o bloco `catch` para que, quando lhe for negado acesso a uma pasta, você possa tentar elevar as permissões e acessá-la novamente. Como regra, capture apenas as exceções que você puder manipular sem deixar seu aplicativo em um estado desconhecido.  
  
 Se você precisar armazenar o conteúdo de uma árvore de diretório, seja na memória ou no disco, a melhor opção é armazenar apenas a propriedade <xref:System.IO.FileSystemInfo.FullName%2A> (do tipo `string`) para cada arquivo. Você pode, então, usar essa cadeia de caracteres para criar um novo objeto <xref:System.IO.FileInfo> ou <xref:System.IO.DirectoryInfo>, conforme necessário ou abra qualquer arquivo que precisar de processamento adicional.  
  
## <a name="robust-programming"></a>Programação robusta  
 O código de iteração de arquivo robusto deve levar em conta muitas complexidades do sistema de arquivos. Para obter mais informações, consulte [Referência técnica de NTFS](http://go.microsoft.com/fwlink/?LinkId=79488).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO>   
 [LINQ e diretórios de arquivos](http://msdn.microsoft.com/library/5a5d516c-0279-4a84-ac84-b87f54caa808)   
 [Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md)
