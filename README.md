## login y register example c++ in console

```c++
#include<iostream>
#include<string>
#include<list>
#include<ctime>

class User{
	private:
		int id;
		std::string username;
		std::string email;
		std::string password;
		bool authenticated;
	public:
		User() : id(0), username(""), email(""), password(""), authenticated(false) {}
		~User() = default;

		bool create(std::string input_username, std::string input_email, std::string input_password){
			id = rand() % 1000 + 1;
			username = input_username;
			email = input_email;
			password = input_password;
			return true;
		}

		int getId(){ return id; }
		std::string getUsername(){ return username; }
		std::string getEmail(){ return email; }
		std::string getPassword(){ return password;}
		bool isAuthenticated(){ return authenticated; }
		void setAutheticated(bool val){ authenticated = val; }
};
int main(){
	char input_option;
	int input_id;
	std::string input_username;
	std::string input_email;
	std::string input_password;
	std::string version = "v1.0";
	std::list<User> users;
	std::list<User>::iterator it;

	srand(time(NULL));

	users.clear();

	while(1)
	{
		system("cls");
		std::cout << "Login Registration System 🧟" << "\t version \n\n" << std::endl;

		for (it = users.begin(); it != users.end(); it++)
		{
			std::string authenticated = it->isAuthenticated() ? "Authenticated" : "not Authenticated";

			std::cout << it->getId() << " | " << it->getUsername() << " | " << it->getEmail() << " | " << it->getPassword() << " | " <<  authenticated << std::endl;
		}
		if (users.empty())
		{
			std::cout << "Add the first user" << std::endl;
		}
		std::cout << std::endl
							<< std::endl;

		std::cout << "[a]dd a New User" << std::endl;
		std::cout << "[v]alidate User" << std::endl;
		std::cout << "[q]uit" << std::endl;

		std::cout << "choice: ";

		std::cin >> input_option;

		if(input_option == 'q'){
			std::cout << "Thanks for use the managment system" << std::endl;
			break;
		}
		else if(input_option == 'a'){
			//The username input
			std::cout << "Enter the username: ";
			std::cin.clear();
			std::cin.ignore();
			std::getline(std::cin, input_username);

			//The email input
			std::cout << "Enter the email: ";
			std::cin.clear();
			std::cin.ignore();
			std::getline(std::cin, input_email);

			//The password input
			std::cout << "Enter the password: ";
			std::cin.clear();
			std::cin.ignore();
			std::getline(std::cin, input_password);

			User newUser;
			newUser.create(input_username, input_email, input_password);
			users.push_back(newUser);
		}
		else if(input_option == 'v'){
			system("cls");
			std::cout << "Enter the email: " << std::endl;
			std::cin >> input_email;

			std::cout << "Enter the password: " << std::endl;
			std::cin >> input_password;

			for (it = users.begin(); it != users.end(); it++)
			{
				if (input_email == it->getEmail() && input_password == it->getPassword())
				{
					it->setAutheticated(true);
					break;
				}
			}
		}
	}
	return 0;
}


```
