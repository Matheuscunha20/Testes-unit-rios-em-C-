# Testes-unit-rios-em-C-using System;
using System.Collections.Generic;
using Xunit;

namespace ProjetoTeste
{
    // Classe de Testes para a classe ValidacoesLista
    public class ValidacoesListaTests
    {
        [Fact]
        public void DeveRemoverNumerosNegativosDeUmaLista()
        {
            // Arrange
            var lista = new List<int> { -5, 3, -1, 9, -2 };
            var validacoes = new ValidacoesLista();

            // Act
            var resultado = validacoes.RemoverNumerosNegativos(lista);

            // Assert
            Assert.Equal(new List<int> { 3, 9 }, resultado);
        }

        [Fact]
        public void DeveConterONumero9NaLista()
        {
            // Arrange
            var lista = new List<int> { 5, 3, 9, 7 };
            var validacoes = new ValidacoesLista();

            // Act
            var resultado = validacoes.ListaContemDeterminadoNumero(lista, 9);

            // Assert
            Assert.True(resultado);
        }

        [Fact]
        public void NaoDeveConterONumero10NaLista()
        {
            // Arrange
            var lista = new List<int> { 5, 3, 9, 7 };
            var validacoes = new ValidacoesLista();

            // Act
            var resultado = validacoes.ListaContemDeterminadoNumero(lista, 10);

            // Assert
            Assert.False(resultado);
        }

        [Fact]
        public void DeveMultiplicarOsElementosDaListaPor2()
        {
            // Arrange
            var lista = new List<int> { 1, 2, 3 };
            var validacoes = new ValidacoesLista();

            // Act
            var resultado = validacoes.MultiplicarNumerosLista(lista, 2);

            // Assert
            Assert.Equal(new List<int> { 2, 4, 6 }, resultado);
        }

        [Fact]
        public void DeveRetornar9ComoMaiorNumeroDaLista()
        {
            // Arrange
            var lista = new List<int> { 1, 9, 3, 5 };
            var validacoes = new ValidacoesLista();

            // Act
            var resultado = validacoes.RetornarMaiorNumeroLista(lista);

            // Assert
            Assert.Equal(9, resultado);
        }

        [Fact]
        public void DeveRetornarOitoNegativoComoMenorNumeroDaLista()
        {
            // Arrange
            var lista = new List<int> { -1, -8, -3 };
            var validacoes = new ValidacoesLista();

            // Act
            var resultado = validacoes.RetornarMenorNumeroLista(lista);

            // Assert
            Assert.Equal(-8, resultado);
        }
    }

    // Classe de Testes para a classe ValidacoesString
    public class ValidacoesStringTests
    {
        [Fact]
        public void DeveRetornar6QuantidadeCaracteresDaPalavraMatrix()
        {
            // Arrange
            var texto = "Matrix";
            var validacoes = new ValidacoesString();

            // Act
            var resultado = validacoes.RetornarQuantidadeCaracteres(texto);

            // Assert
            Assert.Equal(6, resultado);
        }

        [Fact]
        public void DeveContemAPalavraQualquerNoTexto()
        {
            // Arrange
            var texto = "Esse é um texto qualquer";
            var validacoes = new ValidacoesString();

            // Act
            var resultado = validacoes.ContemCaractere(texto, "qualquer");

            // Assert
            Assert.True(resultado);
        }

        [Fact]
        public void NaoDeveConterAPalavraTesteNoTexto()
        {
            // Arrange
            var texto = "Esse é um texto qualquer";
            var validacoes = new ValidacoesString();

            // Act
            var resultado = validacoes.ContemCaractere(texto, "teste");

            // Assert
            Assert.False(resultado);
        }

        [Fact]
        public void TextoDeveTerminarComAPalavraProcurado()
        {
            // Arrange
            var texto = "Começo, meio e fim do texto procurado";
            var validacoes = new ValidacoesString();

            // Act
            var resultado = validacoes.TextoTerminaCom(texto, "procurado");

            // Assert
            Assert.True(resultado);
        }
    }
    
    // Simulação das classes do projeto de console
    public class ValidacoesLista
    {
        public List<int> RemoverNumerosNegativos(List<int> lista)
        {
            return lista.FindAll(x => x >= 0);
        }

        public bool ListaContemDeterminadoNumero(List<int> lista, int numero)
        {
            return lista.Contains(numero);
        }

        public List<int> MultiplicarNumerosLista(List<int> lista, int multiplicador)
        {
            return lista.ConvertAll(x => x * multiplicador);
        }

        public int RetornarMaiorNumeroLista(List<int> lista)
        {
            return lista.Count > 0 ? lista.Max() : throw new InvalidOperationException("A lista está vazia");
        }

        public int RetornarMenorNumeroLista(List<int> lista)
        {
            return lista.Count > 0 ? lista.Min() : throw new InvalidOperationException("A lista está vazia");
        }
    }

    public class ValidacoesString
    {
        public int RetornarQuantidadeCaracteres(string texto)
        {
            return texto.Length;
        }

        public bool ContemCaractere(string texto, string caractere)
        {
            return texto.Contains(caractere);
        }

        public bool TextoTerminaCom(string texto, string caractere)
        {
            return texto.EndsWith(caractere);
        }
    }
}
