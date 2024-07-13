%{ This is a GUI application created with MATLAB's App Designer, enabling users to perform symbolic mathematical operations based on their selection from a drop-down menu. The options include differentiation, integration, Laplace transforms, and inverse Laplace transforms. Depending on the user's choice, the code retrieves the function and parameters from the app's input fields, performs the specified operation using symbolic computation, and displays the result within the app. If the selection is invalid, an error message is shown. This functionality allows users to easily compute and visualize results of various symbolic operations directly within the app interface.# Math_LAB-
Matlab based application.%}

a=app.OPTIONDropDown.Value;
    if  a=="1"
     syms x; % Create symbolic variable
     f = str2sym(app.FunctionEditField.Value);% Get the symbolic expression from the app
     order = app.OrderEditField.Value; % Get the order of differentiation from the app
     result = diff(f,x, order); % Differentiate the function
     app.ResultEditField.Value = char(result); % Display the result
    
    else if a=="2"
    syms x; % Create symbolic variable
    f = str2sym(app.FunctionEditField.Value);% Get the symbolic expression from the app
    order = app.OrderEditField.Value;
    for i=0:order
          if i==0
           result =char(f);  
          else
           result = int(f,x);
           f = result;
     end
     end
     app.ResultEditField.Value = char(result); % Display the result
     elseif a=="3"
        syms t s;
        f = str2sym(app.FunctionEditField.Value);
        % Compute the Laplace transform of the input function
        result= laplace(f, t, s);
    % Display the result
    app.ResultEditField.Value = char(result);
    elseif a=="4"
        syms t s;
        f = str2sym(app.FunctionEditField.Value);
        % Compute the Laplace transform of the input function
        result= ilaplace(f, s, t);
       % Display the result
       app.ResultEditField.Value = char(result);
  else
  app.ResultEditField.Value = "Error!!";
  end
  end
    
