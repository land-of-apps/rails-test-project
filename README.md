# Ruby on Rails Sample Application

## How to run this project

- [Run this project with Docker](#run-this-project-with-docker)
- [Run this project with Docker Compose](#run-this-project-with-docker-compose)
- [Run this project locally](#run-this-project-locally)


### Run this project with Docker

Using the example [Dockerfile](https://github.com/land-of-apps/rails-test-project/blob/master/Dockerfile). Build the container.

```
docker build -t rails-test-project .
```

Run the application with port 3000 forwarding correctly. 

```
docker run -p 3000:3000 -v "$(pwd)":/app -v "$(pwd)"/tmp/appmap:/app/tmp/appmap rails-test-project bundle exec rails server -b 0.0.0.0
```

Or run the tests:

```
docker run -p 3000:3000 -v "$(pwd)":/app -v "$(pwd)"/tmp/appmap:/app/tmp/appmap rails-test-project bundle exec rails test
```

You can then log in as the sample administrative user with the email `example@railstutorial.org` and password `foobar`.

### Run this project with Docker Compose

Using the example [docker-compose.yml](https://github.com/land-of-apps/rails-test-project/blob/main/docker-compose.yml) file in our sample project. Here is the relevant part of the config.

```
services:
  web:
    build: .
    command: bundle exec rails server -b 0.0.0.0
    ports:
      - "3000:3000"
    volumes:
      - .:/app
      - ./tmp/appmap:/app/tmp/appmap
```

Now run this to start the container.

```
docker compose up web
```

You can then log in as the sample administrative user with the email `example@railstutorial.org` and password `foobar`.


### Run this project locally

To get started with the app, clone the repo and then install the needed gems. You can clone the repo as follows:

```
git clone https://github.com/land-of-apps/rails-test-project.git
cd rails-test-project/
```

This project needs the following version of Ruby and Bundler

Ruby: `3.1.2`
Bundler: `2.3.14`

The Ruby installation is system-dependent but we highly recommend [asdf](https://asdf-vm.com/guide/getting-started.html)

Ensure the following commands return the right versions before continuing.

```
$ ruby -v
ruby 3.1.2p20
```

Once Ruby is installed, the `bundler` gem can be installed using the `gem` command:

```
$ gem install bundler -v 2.3.14
```

Confirm the version before continuing.

```
$ bundler --version
Bundler version 2.3.14
```

Then the rest of the necessary gems can be installed with `bundle` (taking care to skip any production gems in the development environment):

```
$ bundle _2.3.14_ config set --local without 'production'
$ bundle _2.3.14_ install
```

If you run into any trouble, you can remove `Gemfile.lock` and rebundle at any time:

```
$ rm -f Gemfile.lock
$ bundle install
```

Next, migrate the database:

```
$ bundle exec rails db:migrate
```

Finally, run the test suite to verify that everything is working correctly:

```
$ bundle exec rails test
```

If the test suite passes, you’ll be ready to seed the database with sample users and run the app in a local server:

```
$ bundle exec rails db:seed
$ bundle exec rails server
```

You can then log in as the sample administrative user with the email `example@railstutorial.org` and password `foobar`.

## License

This is the sample application for the
[*Ruby on Rails Tutorial:
Learn Web Development with Rails*](https://www.railstutorial.org/)
by [Michael Hartl](https://www.michaelhartl.com/).

See also the [6th edition README](https://github.com/learnenough/sample_app_6th_ed#readme).

All source code in the [Ruby on Rails Tutorial](https://www.railstutorial.org/)
is available jointly under the MIT License and the Beerware License. See
[LICENSE.md](LICENSE.md) for details.
