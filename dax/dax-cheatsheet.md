# DAX (Data Analysis Expressions)

## 1. Contextos:

O contexto permite executar análise dinâmica, na qual os resultados de uma fórmula podem ser alterados para refletir a seleção atual de linha ou célula, além de qualquer dado relacionado. Os tipos de contextos existentes são:

    - Contexto de linha: 
    É a “linha atual” da tabela de dados. Se criamos uma fórmula em uma coluna calculada, o contexto de linha para ela inclui todos os valores de todas as colunas na linha atual da tabela de dados. Contextos de linha não são propagados automaticamente através de relacionamentos; ou seja, não é possível acessar diretamente a partir de uma determinada tabela a partir de outra. Acessar esses valores requer funções específicas.
    - Contexto de consulta: 
    Subconjunto de dados que é implicitamente considerado para a avaliação de uma fórmula. O contexto de consulta é definido dentro de uma visualização a partir dos outros campos envolvidos na análise, bem como segmentações e filtros de relatório.
    - Contexto de filtro: 
    Conjunto de valores que são permitidos em cada coluna a partir de restrições de fórmula. A diferença entre este contexto e o contexto de consulta é que o contexto de filtro é definido explicitamente dentro da fórmula, a partir de instruções DAX específicas que veremos mais adiante. O contexto de filtro tem prioridade em relação aos dois contextos vistos anteriormente.