---
title: "-reference (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /reference
dev_langs:
- CSharp
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
caps.latest.revision: 28
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7e33ed084c560470a486ebbb25035a59ddc18565
ms.openlocfilehash: 11bb7fc9490879714542bfbd77a81d58e7d8e8ed
ms.contentlocale: pt-br
ms.lasthandoff: 03/31/2017

---
# <a name="reference-c-compiler-options"></a>/reference (opções do compilador C#)
A opção **/reference** opção faz com que o compilador importe informações de tipo [públicas](../../../csharp/language-reference/keywords/public.md) no arquivo especificado para o projeto atual, permitindo que você referencie metadados nos arquivos do assembly especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/reference:[alias=]filename  
/reference:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O nome de um arquivo que contém um manifesto de assembly. Para importar mais de um arquivo, inclua uma opção **/reference** separada para cada arquivo.  
  
 `alias`  
 Um identificador C# válido que representará um namespace raiz que conterá todos os namespaces no assembly.  
  
## <a name="remarks"></a>Comentários  
 Para importar de mais de um arquivo, inclua uma opção **/reference** para cada arquivo.  
  
 Os arquivos que você importar devem conter um manifesto; o arquivo de saída deve ter sido compilado com uma das opções [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) diferentes de [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **/r** é a forma abreviada de **/reference**.  
  
 Use [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) para importar metadados de um arquivo de saída que não contém um manifesto do assembly.  
  
 Se você referenciar um assembly (Assembly A) que referencia outro assembly (Assembly B), será necessário referenciar o Assembly B se:  
  
-   o tipo A que você usar do Assembly A herdar de um tipo ou implementar uma interface do Assembly B.  
  
-   Você invoca um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B.  
  
 Use [/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) para especificar o diretório no qual uma ou mais das suas referências do assembly estão localizadas. O tópico **/lib** também aborda os diretórios nos quais o compilador pesquisa assemblies.  
  
 Para que o compilador reconheça um tipo em um assembly e não um módulo, ele precisa ser forçado a resolver o tipo, que você pode fazer definindo uma instância do tipo. Há outras maneiras de resolver nomes de tipo em um assembly para o compilador: por exemplo, se você herda de um tipo em um assembly, o nome do tipo será reconhecido pelo compilador.  
  
 Às vezes, é necessário referenciar duas versões diferentes do mesmo componente de dentro de um assembly. Para fazer isso, use a subopção de alias na opção **/reference** para cada arquivo diferenciar entre os dois arquivos. Esse alias será usado como um qualificador do nome do componente e será resolvido para o componente em um dos arquivos.  
  
 O arquivo de resposta csc (.rsp), que referencia assemblies .NET Framework usados com frequência, é usado por padrão. Use [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) se você não desejar que o compilador use csc.rsp.  
  
> [!NOTE]
> No Visual Studio, use a caixa de diálogo **Adicionar Referência**. Para obter mais informações, consulte [Como adicionar ou remover referências usando o Gerenciador de Referências](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Para garantir o comportamento equivalente entre adicionar referências usando `/reference` e usando a caixa de diálogo **Adicionar Referência**, defina a propriedade **Inserir Tipos de Interoperabilidade** como **False** para o assembly que você está adicionando. **True** é o valor padrão para a propriedade.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como usar o recurso [alias externo](../../../csharp/language-reference/keywords/extern-alias.md).  
  
 Compile o arquivo de origem e importe os metadados de `grid.dll` e `grid20.dll`, que foram compilados anteriormente. As duas DLLs contêm versões separadas do mesmo componente e você usa dois **/reference** com opções de alias para compilar o arquivo de origem. As opções têm esta aparência:  
  
 /reference:GridV1=grid.dll e /reference:GridV2=grid20.dll  
  
 Isso configura os aliases externos "GridV1" e "GridV2", que podem ser usados em seu programa por meio de uma instrução externa:  
  
```  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Quando isso for feito, será possível consultar o controle de grade de grid.dll, prefixando o nome do controle com GridV1, assim:  
  
```  
GridV1::Grid  
```  
  
 Além disso, será possível consultar o controle de grade de grid20.dll, prefixando o nome do controle com GridV2, assim:  
  
```  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
