O uso da indexação baseada em caracteres com a propriedade <xref:System.Text.StringBuilder.Chars%2A> pode ser extremamente lento nas seguintes condições:

- A instância de <xref:System.Text.StringBuilder> é grande (por exemplo, ela consiste em várias dezenas de milhares de caracteres).
- O <xref:System.Text.StringBuilder> é "robusto". Ou seja, chamadas repetidas para métodos como <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> expandiram automaticamente a propriedade <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> do objeto e alocaram novos trechos de memória a ela.

O desempenho é afetado gravemente porque cada acesso de caractere percorre toda a lista vinculada de partes para localizar o buffer correto ao qual indexar.

> [!NOTE]
>  Mesmo para um grande objeto <xref:System.Text.StringBuilder> “robusto", usar a propriedade <xref:System.Text.StringBuilder.Chars%2A> para o acesso baseado em índice a um ou um pequeno número de caracteres tem impacto insignificante sobre o desempenho. Normalmente, trata-se de uma operação **0(n)**. O impacto significativo sobre o desempenho ocorre ao iterar os caracteres no objeto <xref:System.Text.StringBuilder>, que é uma operação **O(n^2)**. 

Se encontrar problemas de desempenho ao usar a indexação baseada em caractere com objetos <xref:System.Text.StringBuilder>, você poderá usar qualquer uma das seguintes alternativas:

- Converter a instância <xref:System.Text.StringBuilder> para um <xref:System.String> chamando o método <xref:System.Text.StringBuilder.ToString%2A> e, em seguida, acessar os caracteres na cadeia de caracteres.

- Copiar o conteúdo do objeto <xref:System.Text.StringBuilder> existente para um novo objeto <xref:System.Text.StringBuilder> pré-dimensionado. O desempenho melhora porque o novo objeto <xref:System.Text.StringBuilder> não é robusto. Por exemplo:

   ```csharp
   // sbOriginal is the existing StringBuilder object
   var sbNew = new StringBuilder(sbOriginal.ToString(), sbOriginal.Length);
   ```
   ```vb
   ' sbOriginal is the existing StringBuilder object
   Dim sbNew = New StringBuilder(sbOriginal.ToString(), sbOriginal.Length)
   ```
- Definir a capacidade inicial do objeto <xref:System.Text.StringBuilder> como um valor aproximadamente igual ao seu tamanho máximo esperado chamando o construtor <xref:System.Text.StringBuilder.%23ctor(System.Int32)>. Observe que isso aloca o bloco de memória inteiro mesmo que o <xref:System.Text.StringBuilder> raramente atinja sua capacidade máxima.
