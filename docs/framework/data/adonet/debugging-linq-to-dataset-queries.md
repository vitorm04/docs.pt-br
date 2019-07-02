---
title: Consultas LINQ to DataSet de depuração
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 38eda9f352c4a8d8590e5e57b48c694eadd0397b
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67503990"
---
# <a name="debugging-linq-to-dataset-queries"></a>Consultas LINQ to DataSet de depuração

Visual Studio oferece suporte a depuração do LINQ ao código do conjunto de dados. No entanto, há algumas diferenças entre depuração LINQ no código do conjunto de dados e LINQ para código gerenciado do conjunto de dados. Recursos de depuração mais trabalham com o LINQ para instruções de conjunto de dados, incluindo a depuração, definindo pontos de interrupção e exibir os resultados que são mostrados nas janelas do depurador. No entanto, a execução de consulta adiada em tem alguns efeitos colaterais que devem ser consideradas durante a depuração LINQ ao código do conjunto de dados e existem algumas limitações ao usar Editar e continuar. Este tópico aborda aspectos de depuração que são exclusivos para LINQ to DataSet comparado a não-código do LINQ to DataSet gerenciado.  
  
## <a name="viewing-results"></a>Resultados de exibição  
 Você pode exibir o resultado de uma instrução do conjunto de dados do LINQ usando DataTips, janela de inspeção e a caixa de diálogo QuickWatch. Usando uma janela de origem, você pode pausar o ponteiro em uma consulta na janela de origem e um DataTip aparecerá. Você pode copiar um LINQ para uma variável de conjunto de dados e cole-a janela de observação ou a caixa de diálogo QuickWatch. No LINQ to DataSet, uma consulta não é avaliada quando ela é criada ou declarada, mas somente quando a consulta é executada. Isso é chamado *execução adiada*. Portanto, a variável de consulta não tem um valor até que seja avaliada. Para obter mais informações, consulte [consultas no LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 O depurador deve avaliar uma consulta para exibir os resultados da consulta. Esta avaliação implícita ocorre quando você exibir um LINQ para resultados de consulta de conjunto de dados no depurador, e ele tem alguns efeitos que você deve considerar. Cada avaliação de consulta leva tempo. Expandir o nó de resultados leva tempo. Para algumas consultas, a avaliação repetida pode causar uma caneta visível de desempenho. Avaliar uma consulta também pode causar efeitos colaterais, que são alterações ao valor de dados ou de estado do seu programa. Nem todas as consultas têm efeitos colaterais. Para determinar se uma consulta pode ser avaliada com segurança sem efeitos colaterais, você deve compreender o código que implementa a consulta. Para obter mais informações, consulte [efeitos colaterais e expressões](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Editar e continuar  
 Editar e continuar não suporta alterações ao LINQ em consultas de conjunto de dados. Se você adiciona, remove ou alterar um LINQ para instrução de conjunto de dados durante uma sessão de depuração, será exibida uma caixa de diálogo informa que a alteração não é suportada por editar e continuar. Nesse ponto, você pode desfazer as alterações ou parar a sessão de depuração e reiniciar uma nova sessão com o código editado.  
  
 Além disso, editar e continuar não dá suporte a alteração do tipo ou o valor de uma variável que é usado em uma LINQ to DataSet de instrução. Além disso, você pode desfazer as alterações ou parar e reiniciar a sessão de depuração.  
  
 No Visual C# no Visual Studio, você não pode usar Editar e continuar em qualquer código em um método que contém uma consulta LINQ to DataSet.  
  
 No Visual Basic no Visual Studio, você pode usar Editar e continuar em não-código do LINQ to DataSet, mesmo em um método que contém uma consulta LINQ to DataSet. Você pode adicionar ou remover o código antes do LINQ to DataSet de instrução, mesmo se as alterações afetarem o número de linha da consulta LINQ to DataSet. Sua experiência de depuração para LINQ para o código do conjunto de dados do Visual Basic permanece a mesma como era antes da introdução do LINQ to DataSet. Você não pode alterar, adicionar ou remover uma consulta LINQ to DataSet, no entanto, a menos que você pare a depuração para aplicar as alterações.  
  
## <a name="see-also"></a>Consulte também

- [Depurando código gerenciado](/visualstudio/debugger/debugging-managed-code)
- [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
