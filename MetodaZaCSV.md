public static IEnumerable<(double, double, int, double)> GetPaymentsFromCsv()
        {
            string path = Path.Combine(AppContext.BaseDirectory, "monthly_payments.csv");
            string[] lines = File.ReadAllLines(path);

            // start at 1 because line 0 is the header
            for (int i = 1; i < lines.Length; i++)
            {
                string[] parts = lines[i].Split(',');
                yield return (
                    double.Parse(parts[0], CultureInfo.InvariantCulture),
                    double.Parse(parts[1], CultureInfo.InvariantCulture),
                    int.Parse(parts[2], CultureInfo.InvariantCulture),
                    double.Parse(parts[3], CultureInfo.InvariantCulture));

                    }}
