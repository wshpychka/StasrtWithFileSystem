# StasrtWithFileSystem
Проста програма для роботи з файлами
namespace StartWithFileSystem
{
    class Program
    {
        static void Main(string[] args)
        {

            try
            {
                Console.ForegroundColor = ConsoleColor.Yellow;

                Console.WriteLine("Please enter path to file (include extension):");
                string userPath = Console.ReadLine();
                Console.WriteLine("Please enter text for file: ");
                string userText = Console.ReadLine();
              
                userText += Environment.NewLine;
                if (!File.Exists(userPath))
                {
                    Console.ForegroundColor = ConsoleColor.Red;
                    Console.WriteLine("File doesn't exist, program will be created them!");
                    Console.ForegroundColor = ConsoleColor.Yellow;
                    string fileName = userPath.Substring(userPath.LastIndexOf('\\') + 1);
                    Console.WriteLine($"File {fileName} created!");
                }
                File.AppendAllText(userPath, userText);


            }
            catch (SecurityException ex)
            {
                Console.ForegroundColor = ConsoleColor.Red;
                Console.WriteLine(ex.Message);
                Console.ForegroundColor = ConsoleColor.Yellow;
            }

            catch (Exception ex)
            {
                Console.ForegroundColor = ConsoleColor.Red;
                Console.WriteLine(ex);
                Console.ForegroundColor = ConsoleColor.Yellow;

            }

            
            Console.ReadLine();
        }
    }
