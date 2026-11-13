public static IEnumerable<object[]> InputData
{
    get
    {
        return new[]
        {
    new object[] { new List<double> {1}, new List<double>{1, 2}, new List<int> {1, 2}, 2 },
    new object[] { new List<double> {5, 2}, new List<double>{1}, new List<int> {1, 2}, 2 },
    new object[] { new List<double> {1, 4}, new List<double>{1, 2}, new List<int> {1}, 2 },
};
    }
}


[TestMethod]
[DynamicData(nameof(InputData))]

public void CalculateMonthlyPayment_InvalidInput_ThrowsException(List<double> principalAmounts, List<double> interestRates, List<int> loanTerms, int numberOfLoans)
{
    var db = new DbClass();
    var loanService = new LoanService(db);

    Assert.Throws<ArgumentException>(() => loanService.CalculateMonthlyPayment(principalAmounts, interestRates, loanTerms, numberOfLoans));



}
